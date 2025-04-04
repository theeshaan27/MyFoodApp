package com.example.st10448169_theeshaan_pietersen_imad5112_assignment_12

import android.content.Intent
import android.os.Bundle
import android.widget.Button
import android.widget.EditText
import android.widget.TextView
import androidx.appcompat.app.AppCompatActivity
import kotlin.system.exitProcess

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)  // Sets UI layout for the activity

        // Initialize UI Elements
        val timeOfDayInput = findViewById<EditText>(R.id.editTextText)
        val suggestButton = findViewById<Button>(R.id.button2)
        val resultTextView = findViewById<TextView>(R.id.textView3)
        val resetButton = findViewById<Button>(R.id.button)

        timeOfDayInput.setOnFocusChangeListener { _, hasFocus ->
            if (hasFocus) {
                timeOfDayInput.hint = "" // Remove hint when focused
            } else {
                timeOfDayInput.hint = "Enter Time of Day e.g. morning, afternoon" // Reset hint
            }
        }

        // Set onClickListener for the suggest button
        suggestButton.setOnClickListener {
            val timeOfDay = timeOfDayInput.text.toString().trim()
            val mealSuggestion = getMealSuggestion(timeOfDay) // Call function
            resultTextView.text = mealSuggestion
        }

        // Set onClickListener for the reset button
        resetButton.setOnClickListener {
            restartApp()
        }
    }  // <-- This was incorrectly placed in your code. Now correctly closes onCreate.

    // Function to restart application
    private fun restartApp() {
        val intent = packageManager.getLaunchIntentForPackage(packageName)
        intent?.addFlags(Intent.FLAG_ACTIVITY_CLEAR_TOP or Intent.FLAG_ACTIVITY_NEW_TASK)
        finishAffinity()
        startActivity(intent)
        exitProcess(0)
    }

    // Function to get meal suggestions based on the time of day
    private fun getMealSuggestion(timeOfDay: String): String {
        return when (timeOfDay.lowercase()) {
            "morning" -> "Eggs, cereal, and sausages"
            "mid-morning" -> "Muesli and yogurt"
            "afternoon" -> "Masala steak, wraps"
            "mid-afternoon" -> "Snacks, crisps"
            "dinner" -> "Steak, pasta"
            "after dinner snack" -> "Cheesecake, waffles"
            else -> "Please enter a valid time of day (Morning, Mid-Morning, Afternoon, Mid-Afternoon, Dinner, After Dinner Snack)."
        }
    }
}
