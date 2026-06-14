# 🎵 Melody Stream Bot

A Telegram music bot powered by the JioSaavn API. Search and download high-quality MP3s directly in Telegram.

**Developer:** [@Lawliet7x](https://t.me/Lawliet7x)  
**Channel:** [@public_120](https://t.me/public_120)

---

## ⚙️ Setup

1. **Install dependencies**
   ```bash
   pip install pyTelegramBotAPI requests
   ```

2. **Configure the bot** — open `main.py` and set:
   ```python
   BOT_TOKEN = "your_bot_token_here"
   ADMIN_ID = your_telegram_id
   ```

3. **Run**
   ```bash
   python main.py
   ```

Data is stored locally in `bot_data.json` (auto-created on first run).

---

## 🤖 User Commands

| Command / Button | Description |
|---|---|
| `/start` | Welcome message and main menu |
| `/help` | Usage guide and search tips |
| `/about` | Info about the bot |
| `/stats` | View bot statistics (users, searches, downloads, uptime) |
| `/share` | Share the bot via Telegram or WhatsApp |

---

## 🎵 Music Search & Download

1. Tap **🎵 Search Music** or send `/start` → click the search button
2. Type any song name, artist, or movie name
3. Pick a track from the results list (up to 15 results)
4. The bot downloads and sends it as a 320kbps MP3 audio file

**Search tips:**
- Include artist name for better accuracy: `Believer Imagine Dragons`
- Try movie name for soundtracks: `Animal songs`
- Minimum 2 characters required per query
- 3-second cooldown between searches (rate limiting)

---

## 👑 Admin Commands

Only accessible to the user whose ID is set as `ADMIN_ID`.

| Command | Description |
|---|---|
| `/admin` | Opens the admin panel with command overview |
| `/ping` | Check bot latency and uptime |
| `/stats` | Full stats + admin info section |
| `/broadcast` | Send a message to all registered users |
| `/announce` | Post and pin an announcement in the chat |
| `/backup` | Download a JSON backup of all user data |

---

## 📁 File Structure

```
main.py          # Main bot file
bot_data.json    # Auto-generated data storage (users, stats)
```

Temporary MP3 files are created during download and deleted automatically after sending.

---

## 🔧 Key Technical Details

- **Library:** pyTelegramBotAPI (`telebot`)
- **Mode:** Long polling (no webhook needed)
- **API:** JioSaavn via `https://jiosavanapiryden.vercel.app/api`
- **Audio quality:** Up to 320kbps MP3
- **Storage:** JSON file (no database required)
- **State tracking:** In-memory dict for multi-step search flow
- **Rate limiting:** 3-second cooldown per user between searches

---

## ⚠️ Notes

- Bot token is read directly from `main.py` (not environment variables)
- If a user blocks the bot, broadcast silently skips them
- The bot auto-restarts polling on connection errors
