# Tabula

An autonomous frontend AI controller that builds interactive web interfaces from a single prompt.

## Overview

Tabula is a proof-of-concept single-page application that leverages Large Language Models (LLMs) to dynamically generate and manage a web frontend. You provide it with an API key and an initial instruction, and it autonomously designs, renders, and adds interactivity to the page.

It acts as a browser-based "AI agent" with full control over the DOM, capable of creating complex UIs, handling user interactions, and updating its own state.

## How It Works

The core of Tabula is a continuous loop between the AI and the browser environment:

1.  **Configuration**: On first load, you provide your LLM provider's API endpoint, API key, model name, and an initial instruction (e.g., "Create a to-do list application").
2.  **AI Prompting**: Tabula sends your instruction to the LLM, guided by a system prompt that defines a simple protocol for UI manipulation.
3.  **Response Parsing**: The AI responds with special XML tags:
    *   `<render-html>...</render-html>`: Contains the complete HTML and CSS for the UI. Tabula replaces the entire `<body>` with this content.
    *   `<execute-js>...</execute-js>`: Contains JavaScript code to be executed for adding interactivity, fetching data, or handling events.
4.  **Execution**: The page is rendered, and the scripts are executed.
5.  **Interactive Loop**: The executed JavaScript can call a global `window.trigger(data)` function. This function sends data or event information back to the AI as a new "user" message, allowing the AI to react to user actions and generate an updated UI.

## Features

-   **Zero-Dependency**: Runs entirely from a single `index.html` file. No build tools, servers, or complex setup needed.
-   **Multi-Provider Support**: Compatible with any OpenAI-compatible API (like Groq, DeepSeek) and the Google Gemini native API.
-   **Persistent Configuration**: Saves your API settings in the browser's `localStorage`.
-   **Dynamic UI Generation**: From a simple prompt, it can build out a complete, styled, and functional interface.
-   **Language Adaptation**: The AI is instructed to generate the UI in the same language as the user's initial prompt (e.g., a prompt in Chinese will result in a Chinese UI).

## How to Use

The easiest way to get started is to use the hosted version directly in your browser.

👉 **[Click here to play with Tabula](https://steve02081504.github.io/Tabula)**

### Running Locally

If you prefer to run Tabula from a local file:

1.  Download the `index.html` file from this repository.
2.  Open it in any modern web browser (like Chrome, Firefox, or Edge).
3.  The configuration panel will appear. Fill in your API details (Base URL, API Key, etc.).
4.  Click **"Initialize Environment"** to start.

## Credits

Created by [steve02081504](https://github.com/steve02081504) using [fount](https://github.com/steve02081504/fount).
