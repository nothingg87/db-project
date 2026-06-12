# 現代寵物醫院醫療與營運管理系統 — 前端


## 頁面說明

| 檔案 | 功能 | 對應角色 |
|---|---|---|
| `appointment.html` | 掛號預約 | 櫃檯行政 |
| `medical.html` | 病歷建立 / 開立處方 | 獸醫師 |
| `invoice.html` | 帳單結算 | 櫃檯行政 |
| `owner.html` | 飼主與寵物管理 | 櫃檯行政 |
| `inventory.html` | 庫存查詢 / 目錄管理 | 經理 |
| `schedule.html` | 預約查詢 / 取消 | 櫃檯行政 |

共用邏輯與 Mock 資料層：`common.js`


## 尚未接上後端

## 資料庫架構

```
Owners ──< PetBase ──< Appointments ──< Medical_Records ──< Treatment_Details
                              │                    │
                           Doctors              Invoices
                              │
                           Staff
                        Catalog_Items
```

View：`Pets`（PetBase + 動態計算 Age）

Triggers：
- `trg_td_before_insert`：Historical_Price 強制從 Catalog_Items 覆寫
- `trg_td_after_insert/update/delete`：自動同步 Invoices.Total_Billed
- `trg_mr_after_update`：病歷鎖定時扣減藥品庫存（Item_Category=1）
