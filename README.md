# py3status-ncspot

A plugin for py3status bar that displays and allows you to interact with `ncspot`. `ncspot` is a rust based CLI client for spotify that utilizes the `librespotify` library.

# Install

1. Install the plugin

  ```
  git clone git@github.com:xentrick/py3status-ncspot.git
  cd py3status-ncspot
  mkdir -p ~/.config/i3/py3status
  cp ncspot.py ~/.config/i3/py3status
  ```
2. Add the plugin to your config file. _(This is my personal configuration with Font Awesome)_.

  ```
  order += 'ncspot'
  ```
  ```
  ncspot {
    button_next = 3
    button_play_pause = 1
    button_previous = 2
    format = "\?color=playing  {artist} - {title}  ({time})"
    format_stopped = "   ncspot stopped"
    #format_down = " ncspot not running"

    on_click 1 = "exec py3-cmd refresh ncspot"  # Immediately refresh status on bar
    on_click 2 = "exec py3-cmd refresh ncspot" 
    on_click 3 = "exec py3-cmd refresh ncspot" 
  }
  ```
  
# i3-wm Keybinds 

I also like to bind `ncspot` in i3 using the following configuration changes:

  ```
  # Spotify Binds
  bindsym $mod+p exec dbus-send --print-reply --dest=org.mpris.MediaPlayer2.ncspot /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.PlayPause  > /dev/null
  bindsym $mod+o exec dbus-send --print-reply --dest=org.mpris.MediaPlayer2.ncspot /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Next > /dev/null
  bindsym $mod+i exec dbus-send --print-reply --dest=org.mpris.MediaPlayer2.ncspot /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Previous > /dev/null
  bindsym $mod+O exec dbus-send --print-reply --dest=org.mpris.MediaPlayer2.ncspot /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Forward > /dev/null
  bindsym $mod+I exec dbus-send --print-reply --dest=org.mpris.MediaPlayer2.ncspot /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Rewind > /dev/null
```

__Note: The Forward/Rewind capabilities are something I added to `ncspot` in my fork. See https://github.com/xentrick/ncspot__


