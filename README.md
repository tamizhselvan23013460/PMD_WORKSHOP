# PMD_WORKSHOP

## Develop an android application to create records that store Country names and their respective currencies in the form of a ListView using SQLite DataBase.

## AIM : 
To develop an Android application that uses an SQLite database to store and manage records of country names and their respective currencies, and to display them using a ListView. The application will perform CRUD (Create, Read, Update, Delete) operations through multiple activities, enabling users to add, view, modify, and delete country records efficiently.

## ALGORITHMS :

1. Start the application and initialize required components and user interface elements.

2. Create SQLite database using DatabaseHelper class with required table structure.

3. Define table columns including ID, country name, and corresponding currency fields.

4. Launch CountryListActivity to display all stored country and currency records.

5. Open database connection using DBManager and retrieve all available records.

6. Store retrieved data in list structure and bind it to ListView adapter.

7. Display all country and currency records clearly within the ListView interface.

8. When user clicks Add button, open AddCountryActivity for new data entry.

9. Accept user input for country name and currency, then validate fields properly.

10. Insert validated data into SQLite database and confirm successful insertion message.

11. Refresh ListView in CountryListActivity to reflect newly added database records.

12. When user selects a record, open ModifyCountryActivity with selected details.

13. Allow user to update or delete selected record with proper validation checks.

14. Update or delete data in database and refresh ListView with latest records.

15. Close database connection and terminate application process when user exits.

## PROGRAM :

### Main_Activity :

```

package com.example.workshop1;

import android.content.Intent;
import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;

import com.google.android.material.button.MaterialButton;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        MaterialButton btnViewCountries = findViewById(R.id.btn_view_countries);
        MaterialButton btnAddCountry = findViewById(R.id.btn_add_country);

        btnViewCountries.setOnClickListener(v -> {
            Intent intent = new Intent(MainActivity.this, CountryListActivity.class);
            startActivity(intent);
        });

        btnAddCountry.setOnClickListener(v -> {
            Intent intent = new Intent(MainActivity.this, AddCountryActivity.class);
            startActivity(intent);
        });
    }
}

```

### DataBase Helper :

```

package com.example.workshop1;

import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

public class DatabaseHelper extends SQLiteOpenHelper {

    // Table Name
    public static final String TABLE_NAME = "COUNTRIES";

    // Table columns
    public static final String _ID = "_id";
    public static final String COUNTRY = "country";
    public static final String CURRENCY = "currency";

    // Database Information
    static final String DB_NAME = "WORKSHOP.DB";

    // database version
    static final int DB_VERSION = 1;

    // Creating table query
    private static final String CREATE_TABLE = "create table " + TABLE_NAME + "(" + _ID
            + " INTEGER PRIMARY KEY AUTOINCREMENT, " + COUNTRY + " TEXT NOT NULL, " + CURRENCY + " TEXT);";

    public DatabaseHelper(Context context) {
        super(context, DB_NAME, null, DB_VERSION);
    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        db.execSQL(CREATE_TABLE);
    }

    @Override
    public void onUpgrade(SQLiteDatabase db, int oldVersion, int newVersion) {
        db.execSQL("DROP TABLE IF EXISTS " + TABLE_NAME);
        onCreate(db);
    }
}

```

### Activity_Main.xml :

```
<?xml version="1.0" encoding="utf-8"?>
<!-- Main Dashboard -->
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/bg_color"
    android:gravity="center"
    android:orientation="vertical"
    android:padding="24dp"
    tools:context=".MainActivity">

    <ImageView
        android:layout_width="120dp"
        android:layout_height="120dp"
        android:layout_marginBottom="24dp"
        android:contentDescription="@string/app_logo_description"
        android:src="@android:drawable/ic_dialog_map"
        app:tint="@color/primaryColor" />

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="48dp"
        android:text="@string/app_title"
        android:textColor="@color/primaryDarkColor"
        android:textSize="24sp"
        android:textStyle="bold" />

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btn_view_countries"
        android:layout_width="280dp"
        android:layout_height="60dp"
        android:layout_marginBottom="16dp"
        android:backgroundTint="@color/primaryColor"
        android:text="@string/view_countries"
        android:textColor="@color/white"
        app:cornerRadius="8dp"
        app:icon="@android:drawable/ic_menu_view" />

    <com.google.android.material.button.MaterialButton
        android:id="@+id/btn_add_country"
        style="@style/Widget.MaterialComponents.Button.OutlinedButton"
        android:layout_width="280dp"
        android:layout_height="60dp"
        android:text="@string/add_new_country"
        android:textColor="@color/primaryColor"
        app:cornerRadius="8dp"
        app:icon="@android:drawable/ic_input_add"
        app:strokeColor="@color/primaryColor" />

</LinearLayout>




```


## OUTPUT :

### Main Page :

<img width="1723" height="787" alt="image" src="https://github.com/user-attachments/assets/f7e588cf-f633-4a64-be28-c4b0dc7d9c29" />


### Add Recoreds :

<img width="1729" height="780" alt="image" src="https://github.com/user-attachments/assets/a70cff5c-1e91-452c-8fbb-8563d71f6945" />

### Country Listing Page :

<img width="1707" height="779" alt="image" src="https://github.com/user-attachments/assets/7928d3dc-8243-496b-8564-708be643cf74" />

### Modification Page :

<img width="1715" height="776" alt="image" src="https://github.com/user-attachments/assets/f698c36c-d81c-4d19-9a8d-e9b184b45887" />

### After Modification :

<img width="1664" height="775" alt="image" src="https://github.com/user-attachments/assets/c2732cda-0c9d-40e8-8ee2-2fec9a1788b0" />


## RESULT :

The Android application was successfully developed using SQLite database to store and manage country names along with their respective currencies. The application effectively performed all CRUD operations, allowing users to add, view, update, and delete records through a user-friendly interface. The data was displayed using a ListView, and all database interactions were handled efficiently. Thus, the project met its objective of implementing a functional Android application with SQLite database integration.

