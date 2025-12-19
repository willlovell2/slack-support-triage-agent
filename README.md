# Slack Support Triage Agent

## Overview
This agent monitors a Slack support channel, understands incoming requests, asks clarifying questions when needed, and routes each request to the correct internal channel with a clear summary.

The goal is to reduce manual triage work for SMB owners and teams while keeping humans in control of decisions.

## Who This Is For
- Small and medium-sized businesses
- Teams using Slack for internal or customer support
- Owners who want to save time without adding complexity

## What This Agent Does
- Watches a designated Slack support channel
- Uses AI to understand the intent of each message
- Asks follow-up questions only when required
- Categorizes the request
- Routes a summarized version to the correct Slack channel

## What This Agent Does NOT Do
- It does not solve the issue
- It does not access internal systems
- It does not replace human decision-making

## Architecture (Simple)
This automation uses three parts:

1. **Slack** (where requests come in)
2. **n8n** (the workflow engine that connects everything)
3. **ChatGPT** (the AI brain that classifies and drafts responses)

**Flow:**
Slack message in `#support` → n8n receives it → ChatGPT analyzes it → n8n posts:
- a threaded clarification (if needed)
- a routed summary to the correct channel
