# Finio — Finance Dashboard

A clean, interactive finance dashboard UI built with vanilla JavaScript (no framework dependencies) and modern CSS. Designed with a dark-first aesthetic using a distinctive editorial style.

---

## 🚀 Quick Start

This is a **single-file application** — no build step required.

```bash
# Just open in a browser
open index.html

# Or serve it locally
npx serve .
python3 -m http.server 3000
```

Visit `http://localhost:3000` and you're done.

---

## 📋 Features Overview

### 1. Dashboard Overview
- **4 Summary Cards**: Total Balance, Total Income, Total Expenses, Net Savings — each with a month-over-month change indicator
- **Bar Chart**: Monthly Income vs Expense comparison (custom SVG, no libraries)
- **Line Chart**: Overlapping trend lines for income and expense
- **Spending Breakdown**: Category bars with % and amounts
- **Recent Transactions**: Latest 5 activity items

### 2. Transactions Section
- Full paginated table (10 per page)
- **Search**: Filters by description or category
- **Category filter**: Dropdown to isolate a single category
- **Type filter**: Income / Expense
- **Column sorting**: Click any column header to sort ascending/descending
- **Admin-only**: Add, Edit, Delete transactions via modal

### 3. Role-Based UI (Frontend Simulation)
Roles are toggled via a dropdown in the sidebar:

| Feature | Viewer | Admin |
|---|---|---|
| View dashboard | ✅ | ✅ |
| View transactions | ✅ | ✅ |
| View insights | ✅ | ✅ |
| Add transactions | ❌ | ✅ |
| Edit transactions | ❌ | ✅ |
| Delete transactions | ❌ | ✅ |

### 4. Insights Section
- **Highest Spending Category** with amount and % of total
- **Savings Rate** with contextual advice (target: 20%)
- **Net Income Change** month-over-month
- **Monthly Average Expense** across all months
- **Full Monthly Comparison Table**: Income, Expense, Net per month
- **Complete Category Breakdown** with visual bars

### 5. State Management
All state lives in a single `state` object, managed via a pure re-render pattern:

```js
let state = {
  transactions, role, page, darkMode,
  search, filterCat, filterType,
  sortKey, sortDir, txPage,
  modal, toast
}
```

Changes flow: `state mutation → save() → render()` — no framework needed.

### 6. Optional Enhancements (Implemented)
- ✅ **Dark / Light mode** toggle (persisted)
- ✅ **Data persistence** via `localStorage`
- ✅ **CSV Export** of filtered transactions
- ✅ **Animations**: modal slide-up, card hover lifts, bar transitions
- ✅ **Responsive** design with sidebar collapse on mobile

---

## 🗂 Project Structure

```
finance-dashboard/
├── index.html       # Complete application (single file)
└── README.md        # This document
```

---

## 🎨 Design Decisions

- **Font**: DM Serif Display (headings) + DM Sans (body) — gives a refined editorial feel
- **Color Palette**: Dark #0d0f14 bg with a lime-green `#c8f05a` accent — high-contrast, legible
- **Charts**: Custom SVG — no Chart.js or D3 dependency; fully responsive via `viewBox`
- **Pattern**: Single-state object + full re-render (similar to how early React worked) — simple, predictable, debuggable

---

## 🧪 Mock Data

28 pre-seeded transactions across Jan–Mar 2025 covering categories: Food, Shopping, Transport, Housing, Health, Entertainment, Salary, Freelance, Investment.

All data is editable via the Admin role and persisted to `localStorage`.

---

## 📱 Responsive Breakpoints

| Breakpoint | Layout |
|---|---|
| > 900px | Sidebar visible, 4-column summary grid |
| 500–900px | Sidebar collapsible (hamburger), 2-column grid |
| < 500px | Single column, some table columns hidden |
