# YouTube TV Downloader

Download and organize YouTube channels, playlists, and videos into a TV-show-style media library using `yt-dlp`.

This project is designed for users who want to archive YouTube content locally while keeping it neatly structured and compatible with media center software such as Kodi, Jellyfin, or Plex.

---

## Overview

YouTube TV Downloader is a Python-based utility that downloads videos from YouTube and automatically organizes them into a TV show–style directory structure. Each channel becomes a “TV show,” and videos are treated as episodes within a season.

In addition to downloading videos, the script generates metadata (`.nfo` files) and artwork to make the library easy to browse and index in media managers.

---

## Features

- Download individual videos, playlists, or entire channels
- Automatically organize videos into season folders
- Preserve original video titles
- Generate episode and TV show `.nfo` metadata files
- Download episode posters and fanart
- Skip live streams automatically
- Prevent duplicate downloads using a download archive
- Interactive, queue-based workflow

---

## How It Works

1. The user enters one or more YouTube URLs (video, playlist, or channel).
2. URLs are staged in a queue before downloading.
<img width="2236" height="1259" alt="image" src="https://github.com/user-attachments/assets/368fef32-cbdb-445c-86af-c814fede5769" />
3. The script uses `yt-dlp` to download videos and metadata.
<img width="2236" height="1259" alt="image" src="https://github.com/user-attachments/assets/49419036-4438-44c8-9705-a5e7e0af8e46" />
4. Videos are moved into a season folder (default: `Season 01`).
5. Metadata and artwork are generated for each episode.
6. Temporary folders are cleaned up automatically.
<img width="912" height="601" alt="image" src="https://github.com/user-attachments/assets/1c1cd80c-618c-4088-acd8-6e2d6945773b" />

Each YouTube channel is treated as a TV show, with videos organized as episodes.

---

## Installation

### Requirements

- Python 3.10 or newer
- `yt-dlp`
- A YouTube cookies file (recommended for age-restricted or private content)

### Install Dependencies

```bash
pip install -r requirements.txt
```

If `requirements.txt` is not used:

```bash
pip install yt-dlp
```

---

## Usage

Run the script directly:

```bash
python yt_dl.py
```

### Interactive Commands

- Paste a **video URL** → stages a single video
- Paste a **playlist URL** → prompted for how many videos to download
- Paste a **channel URL or @handle** → prompted for how many recent videos to download
- `go` → start downloading all staged jobs
- `clear` → remove all staged jobs
- `q` / `quit` → exit the program

---

## Configuration

Edit the configuration section at the top of `yt_dl.py`:

```python
BASE_DIR = r"M:\Media\YouTube"
COOKIE_FILE = r"C:\path\to\cookies.txt"
SEASON_NAME = "Season 01"
```

| Variable | Description |
|--------|------------|
| `BASE_DIR` | Root folder where videos are stored |
| `COOKIE_FILE` | Path to your YouTube cookies file |
| `SEASON_NAME` | Season folder name |

---

## Example Output

```
Media/
└── YouTube/
    └── @ExampleChannel/
        ├── tvshow.nfo
        └── Season 01/
            ├── Video Title 1.mp4
            ├── Video Title 1.nfo
            ├── Video Title 1-poster.jpg
            ├── Video Title 1-fanart.jpg
            ├── Video Title 2.mp4
            └── ...
```

---

## Limitations & Notes

- All videos are placed into a single season by default
- Shorts are not handled separately
- Artwork depends on YouTube thumbnail availability
- Error handling is minimal and skips problematic downloads
- Requires valid cookies for some restricted content

---

## Future Improvements

- Multi-season support (by year or playlist)
- Optional Shorts filtering
- Improved error handling and logging
- Command-line arguments instead of interactive input
- Parallel download workers
- Configuration via environment variables

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.
