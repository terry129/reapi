

#RE30 API

# 管理功能
## 參數設定： 
### RE比例與標準上限設定
#### 查詢
```json
GET
/re/parameter/quota
查詢RE比例與標準上限
input : none
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
        {
            "year": 2025,
            "annualQuota": 1400,
            "percentage": 99.00,
            "solarDesc": "太陽能",
            "windOnshoreDesc": "風力(陸域)",
            "windOffshoreDesc": "風力(水域)",
            "hydropowerDesc": "小水力",
            "geothermalDesc": "地熱",
            "modifiedAt": "2025-03-04T13:16:11.01",
            "modifiedBy": 1
        }
}
```

#### 更新
```json
POST
/re/parameter/save
儲存RE比例與標準上限
input : 
{
    "year": 2025,
    "annualQuota": 1400,
    "percentage": 99.00,
    "solarDesc": "太陽能",
    "windOnshoreDesc": "風力(陸域)",
    "windOffshoreDesc": "風力(水域)",
    "hydropowerDesc": "小水力",
    "geothermalDesc": "地熱",
    "modifiedAt": "2025-03-04T13:16:11.01",
    "modifiedBy": 1
}

output :
{
    "pass": true,
    "message": "OK"
}
```


### 參數設定-個別RE用電端年度分配上限設定(參考：管理功能-分配轉供契約設定-RE用電端)
#### 查詢List
```json
GET
input:
{
    "meterNo": null,
    "name": null
}
output:
{
    "pass": true,
    "message": "OK",
    "data": 
        [
            {
                "loadId": 1,
                "annualQuota": 10001,
                "annQuotaModifiedAt": "2025-02-22T07:19:12.15",
                "activatedAt": "2025-02-22",
                "status": 1,
                "modifiedAt": "2025-02-24T11:16:55.287",
                "modifiedBy": 12,
                "nbsCustomerNumber": "07728888917",
                "name": "二一股份有限公司",
                "accountName": "lien"
            },
            {
                "loadId": 5214,
                "annualQuota": 1002,
                "annQuotaModifiedAt": "2025-03-24T10:30:31",
                "activatedAt": null,
                "status": 0,
                "modifiedAt": "2025-02-27T10:29:45.997",
                "modifiedBy": 11,
                "nbsCustomerNumber": "00970301555",
                "name": "山商股份有限公司",
                "accountName": "wanyu"
            }
        ]
}
```


#### RE用電端-更新/儲存
```json
POST
/re/load/save
儲存RE用電端
input: 
{
    "loadId": 5214,
    "annualQuota": 1002,
    "annQuotaModifiedAt": "2025-03-24 10:30:31",
    "activatedAt": null,
    "status": 0
}
output: 
{
    "pass": true,
    "message": "OK"
}
```


## 分配轉供契約設定
### 管理功能-分配轉供契約設定-RE用電端
#### 查詢 List
```json
POST
/re/parameter/load/list
RE用電端年度分配上限設定查詢
input : 
{
    "meterNo": null,
    "name": null
}
output :
{
    "pass": true,
    "message": "OK",
    "data": 
    [
        {
            "loadId": 1,
            "annualQuota": 10001,
            "annQuotaModifiedAt": "2025-03-22T07:19:12.15",
            "activatedAt": "2025-02-22",
            "status": 1,
            "modifiedAt": "2025-03-24T11:16:55.287",
            "modifiedBy": 12,
            "nbsCustomerNumber": "07728888917",
            "name": "二一股份有限公司",
            "accountName": "lien"
        },
        {
            "loadId": 5214,
            "annualQuota": 1002,
            "annQuotaModifiedAt": "2025-03-24T10:30:31",
            "activatedAt": "2025-02-22",
            "status": 0,
            "modifiedAt": "2025-03-05T11:28:44.557",
            "modifiedBy": 1,
            "nbsCustomerNumber": "00970301555",
            "name": "山商股份有限公司",
            "accountName": "lien"
        }
    ]
}
```


#### 電號 list 
```json
RE用電端電號List
GET 
/re/load/nbscustnumber/exclude-re
input: none
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
    [
        "00010225109",
        "00012223509",
        "00018226086",
        "00020222106",
        "00020226108",
        "00020222201"
    ]
}
```

#### single 電號查詢 
```json
GET
/re/load/nbscustnumber/{nbscustnumber}
RE用電端查詢By電號
input : none
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
        {
            "loadId": 4354,
            "annualQuota": null,
            "annQuotaModifiedAt": null,
            "activatedAt": null,
            "status": 1,
            "modifiedAt": null,
            "modifiedBy": null,
            "nbsCustomerNumber": "30023642381",
            "name": "小莫股份有限公司",
            "accountName": null
        }
}
```


#### RE用電端-更新/儲存
```json
POST
/re/load/save
儲存RE用電端
input: 
{
    "loadId": 5214,
    "annualQuota": 1002,
    "annQuotaModifiedAt": "2025-03-24 12:30:31",
    "activatedAt": "2025-03-24",
    "status": 0
}
output: 
{
    "pass": true,
    "message": "OK"
}
```


#### RE用電端 - 查詢 by ID
```json
GET
/re/load/single/{id}
RE用電端查詢By ID
input : none 
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
        {
            "generatorId": 1281,
            "reFuelTypeId": 1,
            "activatedAt": "2024-12-30",
            "status": 0,
            "modifiedAt": "2025-03-07T09:48:14.033",
            "modifiedBy": 12,
            "nbsCustomerNumber": "1088006",
            "name": "XXX",
            "reFuelTypeName": "太陽能",
            "accountName": "yyy"
        }
}
```

### 管理功能-分配轉供契約設定-RE發電端：
#### 查詢 List
```json
POST
/re/generator/list
RE發電端查詢
input : 
{
    "meterNo": null,
    "name": null
}
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
        [
            {
                "generatorId": 1281,
                "reFuelTypeId": 1,
                "activatedAt": "2024-12-30",
                "status": 0,
                "modifiedAt": "2025-03-07T09:48:14.033",
                "modifiedBy": 12,
                "nbsCustomerNumber": "108006",
                "name": "xxxx",
                "reFuelTypeName": "太陽能",
                "accountName": "yyy"
            }
        ]
}
```

#### 電號 list
```json
GET
/re/generator/nbscustnumber/exclude-re
查詢非RE發電端電號
input : none
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
        [
            "00216512894",
            "00315883890",
            "00412680892",
            "01217902844",
            "01611562842"
        ]
}
```

#### by single 電號 - RE發電端
```json
GET
/re/generator/nbscustnumber/{nbscustnumber}
RE發電端查詢By電號
input : none 
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
        {
            "generatorId": 538,
             "reFuelTypeId": null,
            "activatedAt": null,
            "status": 1,
            "modifiedAt": null,
            "modifiedBy": null,
            "nbsCustomerNumber": "01292345044",
            "name": "波卡股份有限公司",
            "reFuelTypeName": null,
            "accountName": null
        }
}
```

#### RE發電端-更新/儲存
```json
POST
/re/generator/save
儲存RE發電端
input:
{
    "generatorId": 1281,
    "reFuelType": "太陽能",
    "activatedAt": "2024-12-30",
    "status": 1
}

output:
{
    "pass": true,
    "message": "OK"
}
```


#### RE發電端 - 查詢 by ID
```json
GET
/re/generator/single/{id}
RE用電端查詢By ID
input : none 
output : 
{
    "pass": true,
    "message": "OK",
    "data": 
        {
            "generatorId": 1281,
            "reFuelTypeId": 1,
            "activatedAt": "2024-12-30",
            "status": 0,
            "modifiedAt": "2025-03-07T09:48:14.033",
            "modifiedBy": 12,
            "nbsCustomerNumber": "108006",
            "name": "xxxx",
            "reFuelTypeName": "太陽能",
            "accountName": "yyy"
        }
}
```


#### 查詢所有RE能源別
```json
GET
/re/generator/fueltypes
查詢所有RE能源別
input : none 
output :
{
    "pass": true,
    "message": "OK",
    "data": 
        [
            {
                "id": 1,
                "name": "太陽能",
                "orderNum": 1
            },
            {
                "id": 2,
                "name": "風力(陸域)",
                "orderNum": 2
            },
            {
                "id": 3,
                "name": "風力(水域)",
                "orderNum": 3
            },
            {
                "id": 4,
                "name": "小水力",
                "orderNum": 4
            },
            {
                "id": 5,
                "name": "地熱",
                "orderNum": 5
            }
        ]
}

```



## glossary  
```
annualQuota : 年度分配上限
percentage : RE分配比例
modifiedAt : 更新時間
modifiedBy : 更新人員
solarDesc : 太陽能說明
windOnshoreDesc : 風力(陸域)說明
windOffshoreDesc : 風力(水域)說明
hydropowerDesc : 小水力說明
geothermalDesc : 地熱說明
meterNo : 表號
name : 發電端名稱 / 用電端名稱 
accountName : 更新人員名稱
generatorId: 發電端 ID
reFuelTypeId: 能源別
reFuelTypeName: 能源別名稱
activatedAt: 加入RE起始月份
status: 參與RE用電端狀態
nbsCustomerNumber: 電號
accountName: 更新人員名稱
loadId: 用電端 ID
annQuotaModifiedAt: 年度分配上限-更新時間
```


