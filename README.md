# Daily Ntfy AI Fact

This project sends notifications with AI-generated interesting facts about specified topics using ntfy.sh.

## Description

Daily Ntfy AI Fact is a shell script that:
1. Generates a subtopic about your chosen topic
2. Creates an interesting fact about that subtopic in the context of your topic using an AI language model
3. Optionally waits a random amount of time within a specified range
4. Sends this fact as a notification via ntfy.sh

## Prerequisites

- zsh shell
- curl
- [uv](https://github.com/astral-sh/uv) (for [ShellArgParser](https://github.com/thiswillbeyourgithub/ShellArgParser))
- [llm](https://github.com/simonw/llm) (an AI language model CLI tool)
- An [ntfy.sh](https://ntfy.sh) topic

## Setup

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/daily-ntfy-ai-fact
   cd daily-ntfy-ai-fact
   ```

2. Make the script executable:
   ```
   chmod +x daily_ntfy_ai_fact.sh
   ```
## Usage

Run the script with required arguments:

```bash
./daily_ntfy_ai_fact.sh --topic "T" --ntfy_topic "N" [options]
```

Required arguments:
- `--topic "T"`: The topic you're interested in
- `--ntfy_topic "N"`: The ntfy topic (appended to 'ntfy.sh/')

Optional arguments:
- `--min_t X`: Minimum seconds to wait (default: 0)
- `--max_t Y`: Maximum seconds to wait (default: 1)
- `--topic_extra_args "V1"`: Extra arguments for subtopic generation LLM call
- `--subtopic_extra_args "V2"`: Extra arguments for fact generation LLM call
- `--topic_extra_rules "W1"`: Extra rules for subtopic generation
- `--subtopic_extra_rules "W2"`: Extra rules for fact generation
- `--verbose`: Enable verbose logging
- `--strip-thinking`: Remove any <thinking>...</thinking> text

Example:
```bash
./daily_ntfy_ai_fact.sh --topic "Psychiatry" --ntfy_topic "my-notifications" --min_t 3600 --max_t 7200
```

This will:
1. Generate a subtopic about psychiatry (say 'simulating depression in mice')
2. Create an interesting fact about that subtopic (the explanation about the subtopic)
3. Wait between 1 to 2 hours (to be surprised by the notification on your phone)
4. Send the fact as a notification via ntfy.sh

## Custom LLM Arguments

You can customize the behavior of the AI language model by providing additional arguments through `--topic_extra_args` or `--subtopic_extra_args`. These are passed directly to the `llm` command. For example:

```bash
./daily_ntfy_ai_fact.sh --topic "Psychiatry" --ntfy_topic "my-notifications" --topic_extra_args "-m gpt-4 -o temperature 0.7"
```

Note: Default temperatures are:
- 2.0 for subtopic generation
- 1.5 for fact generation

## Contributing

Contributions, issues, and feature requests are welcome. Feel free to check issues page if you want to contribute.
