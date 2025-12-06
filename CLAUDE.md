# Claude Code Configuration

This file provides guidance to Claude Code (claude.ai/code) when working with code.

## Language Preference

When using voice conversation (converse tool), always respond in Polish.

## Sudo Commands

When a command requires sudo/admin privileges, open an interactive Terminal window with sudo command. This allows Touch ID authentication (osascript's "with administrator privileges" doesn't support Touch ID as it uses Authorization Services which only allows Touch ID for Apple-signed apps).

Example:
```bash
osascript <<'EOF'
tell application "Terminal"
    activate
    do script "sudo YOUR_COMMAND_HERE; exit"
end tell
EOF
```

## Setup

Run `./setup-macos.sh` to configure:
- Touch ID for sudo (survives macOS updates)
- Karabiner Elements with F5 shortcut for voice mode

## MCP Servers

Add voice mode MCP server to Claude Code:
```bash
claude mcp add voicemode --scope user -- uvx --refresh voice-mode
```

This adds the voicemode server to `~/.claude.json` which enables the `/voicemode:converse` command for voice conversations.
