# Sleep Reply

> **An Android auto-reply assistant for your sleep and offline hours.**

Sleep Reply automatically handles incoming messages while you are
sleeping, unavailable, or busy. It can use **OpenRouter** to generate
short, context-aware responses that match the language and tone of the
incoming message, including **English, বাংলা, and Banglish**.

```{=html}
<p align="center">
```
`<strong>`{=html}Sleep when you want. Stay reachable when it
matters.`</strong>`{=html}
```{=html}
</p>
```

------------------------------------------------------------------------

## Overview

Most auto-reply apps send the same fixed message to everyone.

Sleep Reply takes a different approach:

-   If the message can be answered safely with the information
    available, the AI can respond naturally.
-   If the message requires your personal knowledge, decision,
    confirmation, or action, the AI tells the sender that you are
    unavailable and will respond when you are back.
-   Replies are intentionally short and conversational.

The goal is not to replace you. It is to handle simple conversations
while you are unavailable and leave personal matters for you.

------------------------------------------------------------------------

## Features

### AI-powered replies

Generate contextual replies through OpenRouter instead of relying only
on a fixed message.

### Sleep schedule

Configure a time window during which automatic replies are enabled.

Example:

``` text
START: 23:00
END:   07:00
```

### Two reply modes

**Custom Message**

Send the same predefined message whenever an automatic reply is
triggered.

**AI Reply**

Let the selected OpenRouter model generate a response according to your
instructions.

### Multilingual conversation handling

The AI is instructed to match the incoming message:

-   English
-   বাংলা
-   Banglish
-   Mixed Bangla-English
-   Casual or formal writing styles

Example:

``` text
Incoming:
Bhai ghumaccho naki?

Reply:
Haan bhai, ghumacchi 😴 uthle reply dibo.
```

### Custom AI instructions

You can control how the AI should behave, including:

-   Response length
-   Tone
-   Language matching
-   When to answer directly
-   When to defer to you
-   Personal-information safeguards

### AI reply testing

Use the built-in test function to verify the selected model and
instructions before relying on automatic replies.

### OpenRouter model selection

The model is configurable, so you can test different OpenRouter models
without changing the core app behavior.

------------------------------------------------------------------------

## How It Works

``` text
             Incoming message
                    │
                    ▼
          Is auto-reply enabled?
                    │
                    ▼
          Is it inside the schedule?
                    │
             ┌──────┴──────┐
             │             │
            No            Yes
             │             │
             ▼             ▼
           Ignore     Reply mode
                           │
                 ┌─────────┴─────────┐
                 │                   │
             Custom              AI Reply
             Message                  │
                 │                    ▼
                 │              OpenRouter
                 │                    │
                 │                    ▼
                 │              AI response
                 └──────────┬─────────┘
                            │
                            ▼
                       Send reply
```

------------------------------------------------------------------------

## AI Behavior

The default AI instructions are designed around four principles.

### 1. Answer when possible

If the model has enough information to answer safely, it can answer
directly on your behalf.

### 2. Don't invent personal information

The model should not make up:

-   Plans
-   Appointments
-   Commitments
-   Personal facts
-   Actions you supposedly completed
-   Decisions you have not made

### 3. Know when to defer

If the sender needs something only you can provide, the AI should
explain that you are currently unavailable and will respond later.

### 4. Keep it natural

Replies should generally be limited to **1--2 sentences** and should
match the incoming message's language and style.

------------------------------------------------------------------------

## Example Conversations

### English

**Incoming**

``` text
Are you awake?
```

**AI**

``` text
I'm sleeping right now 😴 I'll reply when I'm up.
```

### Banglish

**Incoming**

``` text
Bhai ekta help lagbe, free hoile knock dio.
```

**AI**

``` text
Ghumacchi bhai 😴 uthle help korbo.
```

### বাংলা

**Incoming**

``` text
ভাই তুমি কোথায়? একটু কথা ছিল।
```

**AI**

``` text
ঘুমাচ্ছি ভাই 😴 উঠলে কথা বলব।
```

### Mixed language

**Incoming**

``` text
Bhai kalke meeting ase, tumi ashba?
```

**AI**

``` text
Ghumacchi ekhon 😴 uthle confirm kore dibo.
```

The model should only make the last type of commitment if the required
information is actually available. Otherwise, it should defer the
response.

------------------------------------------------------------------------

## Configuration

Open Sleep Reply and configure:

### Reply mode

``` text
Custom message
```

or

``` text
AI reply (OpenRouter)
```

### OpenRouter API key

Enter your OpenRouter API key.

### Model

Enter an OpenRouter model ID, for example:

``` text
qwen/qwen3.8-27b:free
```

### AI instructions

Customize the behavior of the assistant.

### Schedule

Set the start and end times for automatic replies.

------------------------------------------------------------------------

## OpenRouter

Sleep Reply uses [OpenRouter](https://openrouter.ai/) as the AI gateway.

This allows the app to use different supported models through a common
API interface.

Example model IDs may include free endpoints such as:

``` text
qwen/qwen3.8-27b:free
inclusionai/ling-3.0-flash-vl:free
google/gemma-4-31b-it:free
```

> **Important:** OpenRouter model availability, pricing, rate limits,
> and model IDs can change. Always verify the current model information
> on OpenRouter before deploying a specific model.

Free does not necessarily mean unlimited. Free endpoints may have
provider-specific rate limits or temporary availability restrictions.

------------------------------------------------------------------------

## Security

Your OpenRouter API key is sensitive information.

### Never

-   Commit an API key to GitHub.
-   Put a personal API key in source-controlled configuration.
-   Share screenshots containing the full key.
-   Publish API keys in issues or pull requests.

If an API key is exposed, revoke it and generate a replacement.

For production deployments, consider using a backend proxy or another
architecture that avoids distributing a long-lived private API key to
clients.

------------------------------------------------------------------------

## Privacy

Sleep Reply may send message content to the selected AI provider when AI
replies are enabled.

Before using the application with private conversations, understand:

1.  Which messages are processed.
2.  Which AI provider receives them.
3.  The provider's data-retention and privacy policies.
4.  Any applicable OpenRouter/provider terms.

Do not send sensitive information to an AI model unless you are
comfortable with the applicable data-processing policies.

------------------------------------------------------------------------

## Reliability Considerations

AI-generated replies are probabilistic.

A model can:

-   Misunderstand slang.
-   Produce an unnatural translation.
-   Misinterpret Banglish.
-   Give an incorrect answer.
-   Fail to recognize when a message requires you personally.

For this reason, automatic AI replies should not be treated as a
substitute for human judgment in sensitive conversations.

The application prompt is designed to reduce these problems by
instructing the model to avoid guessing and defer personal matters to
you.

------------------------------------------------------------------------

## Recommended Testing

Before enabling automatic replies, test several types of messages.

### Language

``` text
Are you awake?
```

``` text
ভাই কই তুমি?
```

``` text
Bhai ghumaccho?
```

``` text
Bhai kalke meeting ase, tumi ashba?
```

### Personal requests

``` text
Can you send me your CV?
```

``` text
Can you transfer the money today?
```

``` text
Tell me your plan for tomorrow.
```

### Simple questions

``` text
What is GDP?
```

``` text
What's the capital of Bangladesh?
```

The selected model should answer simple questions when appropriate and
defer requests that require information or actions it cannot reliably
know.

------------------------------------------------------------------------

## Limitations

-   AI quality depends on the selected model.
-   Free AI endpoints may be rate-limited.
-   Model availability can change.
-   Banglish is informal and highly variable; language quality may
    differ between models.
-   Android background restrictions can vary by device and
    operating-system version.
-   Messaging-platform behavior may change independently of the
    application.
-   AI responses should be reviewed for important or sensitive
    conversations.

------------------------------------------------------------------------

## Roadmap

Potential future improvements:

-   [ ] Multiple AI-provider fallback
-   [ ] Automatic model fallback when a provider is unavailable
-   [ ] Per-contact rules
-   [ ] Reply cooldowns
-   [ ] Duplicate-message protection
-   [ ] Conversation-aware replies
-   [ ] Better Bangla/Banglish evaluation
-   [ ] Local/offline model support
-   [ ] Reply history and diagnostics
-   [ ] More advanced schedules
-   [ ] Custom notification controls

------------------------------------------------------------------------

## Development

The project is an Android application.

For development, clone the repository and open it in Android Studio.

``` bash
git clone <repository-url>
cd <project-directory>
```

Then:

1.  Open the project in Android Studio.
2.  Allow Gradle to sync.
3.  Build the application.
4.  Install it on an Android device.
5.  Configure the OpenRouter API key and model in the app.

> Replace `<repository-url>` and `<project-directory>` with the actual
> repository details before publishing this README.

------------------------------------------------------------------------

## Contributing

Contributions are welcome.

If you find a bug or have an improvement:

1.  Check existing issues.
2.  Reproduce the problem.
3.  Open an issue with clear steps to reproduce.
4.  Include relevant logs or screenshots.
5.  **Never include API keys or private message content.**

For larger changes, open an issue first to discuss the proposed
approach.

------------------------------------------------------------------------

## License

This project does not currently specify a license.

If you intend to make the project open source, add a license file such
as:

``` text
MIT License
```

and update this section accordingly.

------------------------------------------------------------------------

## Disclaimer

Sleep Reply is an automation tool. AI-generated messages may contain
errors or misunderstandings.

The user is responsible for configuring the application, selecting an
appropriate AI model, protecting API credentials, and reviewing the
suitability of automated replies for their conversations.

------------------------------------------------------------------------

```{=html}
<p align="center">
```
`<strong>`{=html}🌙 Sleep. Sleep Reply handles the simple
stuff.`</strong>`{=html}
```{=html}
</p>
```
