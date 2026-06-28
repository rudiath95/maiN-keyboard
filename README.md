# MaiN_Keyboard

An on-screen keyboard for KDE Plasma / Wayland that actually works.

> **Note:** This fork is configured for **US (ANSI QWERTY) keyboard layout** with a function key row (Esc + F1–F12). All other layouts have been removed.

## Why MaiN_Keyboard?

Many on-screen keyboards have issues under Wayland:
- Focus gets stolen from text fields
- Keystrokes don't arrive
- Complicated configuration required

**MaiN_Keyboard solves these problems** through:
- XWayland mode with special window flags
- Kernel-level keyboard input via uinput
- No focus stealing - text fields stay active

## Features

- **Works under Wayland** - Uses uinput for reliable keyboard input
- **No focus stealing** - Text fields remain active while typing
- **Dark design** - Modern iOS-style buttons with 3D shadow effect
- **Adjustable opacity** - Set transparency (50%-100%) via tray menu
- **Single US layout** - Standard US ANSI QWERTY with function key row
- **Layout switching** - Button in title bar or via tray menu (single layout—no-op)
- **Scalable** - Three sizes: S (100%), M (120%), B (160%)
- **Monitor switching** - Move active window between monitors
- **System Tray** - Minimizes to taskbar
- **Saves settings** - Remembers size, layout, and opacity
- **Movable** - Window can be freely positioned

## Screenshot

![MaiN_Keyboard](https://i.ibb.co/RTxm3ypq/Bildschirmfoto-20260127-034035.png)

## Installation

### Manual Installation (recommended)

This is a custom fork — not available in AUR. Install manually:

> [!IMPORTANT]
> After installation, add your user to the `input` group and then log out and back in:
> ```bash
> sudo usermod -aG input $USER
> ```

**Install dependencies:**
```bash
sudo pacman -S python-pyqt6 python-evdev
```

**Clone this fork:**
```bash
git clone https://github.com/rudiath95/maiN-keyboard.git
cd maiN-keyboard
```

**Install:**
```bash
sudo make install
```

**Or run directly:**
```bash
python3 main.py
```

### uinput Permission

MaiN_Keyboard requires access to `/dev/uinput`. If needed:

```bash
# Set permission once
sudo setfacl -m u:$USER:rw /dev/uinput

# Or permanently via udev rule
echo 'KERNEL=="uinput", MODE="0666"' | sudo tee /etc/udev/rules.d/99-uinput.rules
sudo udevadm control --reload-rules
sudo udevadm trigger
```

## Usage

| Action | Description |
|--------|-------------|
| **Drag title bar** | Move window |
| **US** | US keyboard layout (only option) |
| **S / M / B** | Change size (Small/Medium/Big) |
| **<- / ->** | Move active window to other monitor |
| **✕** | Minimize to system tray |
| **Tray icon left-click** | Show/hide keyboard |
| **Tray icon right-click** | Menu with layout selection |

## Technical Details

- **GUI:** PyQt6
- **Input:** python-evdev (uinput)
- **Display:** XWayland (for focus handling)
- **Config:** `~/.config/osk/settings.json`

## License

MIT License

## Authors

- **MaiN** — Original author ([cachyOSMaiN/maiN-keyboard](https://github.com/cachyOSMaiN/maiN-keyboard))
- **rudiath95** — This fork (US layout with function key row)

---

**Keywords:** on-screen keyboard Linux, virtual keyboard KDE Plasma, Wayland on-screen keyboard, OSK Wayland, touchscreen keyboard Linux, software keyboard KDE, on-screen keyboard Python, uinput keyboard Linux, XWayland keyboard, on-screen keyboard Arch Linux, US keyboard layout, function keys F1-F12, accessibility keyboard KDE
