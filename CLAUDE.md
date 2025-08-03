# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a **Financial Command Center** - a single-page web application for personal financial management. The application is built as a standalone HTML file with embedded CSS and JavaScript, designed for simplicity and portability.

## Architecture

- **Single File Application**: Everything is contained in `index.html` (2,225 lines)
- **No Build Process**: Direct HTML/CSS/JavaScript - no compilation or bundling required
- **Client-side Storage**: Uses `localStorage` for data persistence
- **Responsive Design**: Mobile-friendly with CSS Grid and Flexbox
- **Theme Support**: Light/dark mode toggle with CSS custom properties

## Core Components

### Data Model (`FinancialData` class - line 1419)
- **Income Sources**: Recurring income with frequency (weekly, bi-weekly, monthly, annual)
- **Fixed Expenses**: Recurring expenses like mortgage, utilities
- **Subscriptions**: Service subscriptions (Netflix, Spotify, etc.)
- **Monthly Variables**: Budget Buddy tracking and other variable expenses
- **Settings**: Savings goals, budget limits, theme preferences

### Main Features
1. **Dashboard**: Overview metrics, savings progress, Budget Buddy status
2. **Income Management**: Add/edit/toggle income sources
3. **Expense Tracking**: Fixed expenses and subscriptions
4. **Monthly Variables**: Budget Buddy and variable expense tracking
5. **Analytics**: Savings trends, expense breakdown, YTD summaries
6. **Data Management**: Import/export functionality

### Key JavaScript Functions
- `updateDashboard()` (line 1605): Recalculates and displays all metrics
- `calculateMonthlyAmount()` (line 1445): Converts different frequencies to monthly amounts
- `renderIncomeList()`, `renderExpensesList()`, `renderSubscriptionsList()`: Update UI lists
- `drawLineChart()`, `drawPieChart()` (lines 1277, 1365): Custom chart rendering

## Development Workflow

### Running the Application
```bash
# Open in browser - no server required
open index.html
```

### Testing
- No formal test suite - manual testing in browser
- Test data persistence by refreshing the page
- Verify responsive design across different screen sizes

### Data Structure
The application stores data in localStorage with this structure:
```javascript
{
  income: [],           // Array of income sources
  expenses: [],         // Array of fixed expenses  
  subscriptions: [],    // Array of subscriptions
  monthlyVariables: {}, // Object with month keys
  settings: {},         // User preferences
  currentMonth: "YYYY-MM" // Current viewing month
}
```

## Key Implementation Details

- **Month Navigation**: Users can navigate between months to view historical data
- **Frequency Conversion**: All amounts are normalized to monthly for calculations
- **Budget Buddy**: Special category for discretionary spending with $750 default limit
- **Chart Rendering**: Custom lightweight chart implementation (no external libraries)
- **Modal System**: JavaScript-based modals for data entry forms
- **Theme System**: CSS custom properties with localStorage persistence

## Common Tasks

### Adding New Features
1. Add HTML structure in appropriate tab section
2. Create JavaScript functions for data manipulation
3. Update relevant render functions to display new data
4. Ensure data persistence by calling `financialData.save()`

### Styling Updates
- All styles are in the `<style>` section (lines 7-811)
- Uses CSS custom properties for theming
- Responsive design with CSS Grid and Flexbox

### Data Migration
- Export/import functionality available in Settings tab
- Data format is JSON - can be manually edited if needed