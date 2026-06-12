---
title: "Using cron or at with rhythmbox?"
date: 2006-05-08
forum: Absolute Beginner Talk
---

### Post by gr0kzer0 on 2006-05-08
I use rhythmbox to play music on my laptop.

I'd like to use it as an alarm clock - ie, set the computer to wake me up at a certain time with some music. I've been reading about the "at" and "cron" commands. But they seem to be just for console-interface commands.

Is there a way of using cron or at with X-windows apps? Or is there another way to set Rhythmbox (and maybe other apps in the GUI) to start up at a certain time?

---

### Post by cgjones on 2006-05-08
Type the following line in the terminal to see what options Rhythmbox supports.
```
rhythmbox --help
```

I think that you should be able to start Rhythmbox from the command line, provided that it has the options to do so. See what options are available, and post them here if you want. I'm not at my Ubuntu machine right now, so I'm kind of limited in what I can try.

---

### Post by gr0kzer0 on 2006-05-08
```
t0p@lapt0p:~$ rhythmbox --help
Usage: rhythmbox [OPTION...]
  --load-modules=MODULE1,MODULE2,...     Dynamic modules to load

Help options
  -?, --help                             Show this help message
  --usage                                Display brief usage message

Application options
  --print-playing                        Print the playing song and exit
  --print-playing-artist                 Print the playing song artist and exit
  --print-playing-album                  Print the playing song album and exit
  --print-playing-track                  Print the playing song track and exit
  --print-playing-genre                  Print the playing song genre and exit
  --print-playing-path                   Print the playing song URI and exit
  --print-song-length                    Print the playing song length in
                                         seconds and exit
  --print-play-time                      Print the current elapsed time of
                                         playing song and exit
  --set-play-time=LONG                   Seek to the specified time in playing
                                         song if possible and exit
  --seek=LONG                            Seek by the specified amount if
                                         possible and exit
  --set-rating=DOUBLE                    Set the rating of the currently
                                         playing song and exit
  --play-pause                           Toggle play/pause mode
  --pause                                Pause playback if currently playing
  --play                                 Resume playback if currently paused
  --focus                                Focus the running player
  --previous                             Jump to previous song
  --next                                 Jump to next song
  --shuffle                              Toggle shuffling
  --repeat                               Toggle repeat
  --set-volume=FLOAT                     Set the volume level
  --toggle-mute                          Mute or unmute playback
  --toggle-hide                          Change visibility of the main
                                         Rhythmbox window
  -d, --debug                            Enable debugging code
  --no-update                            Do not update the library
  -n, --no-registration                  Do not register the shell
  --dry-run                              Don't save any data permanently
                                         (implies --no-registration)
  --rhythmdb-file=STRING                 Path for database file to use
  -q, --quit                             Quit Rhythmbox

GStreamer
  --gst-version                          Print the GStreamer version
  --gst-fatal-warnings                   Make all warnings fatal
  --gst-debug-help                       Print available debug categories and
                                         exit
  --gst-debug-level=LEVEL                Default debug level from 1 (only
                                         error) to 5 (anything) or 0 for no
                                         output
  --gst-debug=LIST                       Comma-separated list of
                                         category_name:level pairs to set
                                         specific levels for the individual
                                         categories. Example:
                                         GST_AUTOPLUG:5,GST_ELEMENT_*:3
  --gst-debug-no-color                   Disable coloured debugging output
  --gst-debug-disable                    Disable debugging
  --gst-disable-cpu-opt                  Disable accelerated CPU instructions
  --gst-plugin-spew                      Enable verbose plugin loading
                                         diagnostics
  --gst-plugin-path=PATHS                path list for loading plugins
                                         (separated by ':')
  --gst-plugin-load=PLUGINS              Comma-separated list of plugins to
                                         preload in addition to the list
                                         stored in environment variable
                                         GST_PLUGIN_PATH
  --gst-disable-segtrap                  Disable trapping of segmentation
                                         faults during plugin loading
  --gst-scheduler=SCHEDULER              Scheduler to use (default is 'opt')
  --gst-registry=REGISTRY                Registry to use

GTK+
  --gdk-debug=FLAGS                      Gdk debugging flags to set
  --gdk-no-debug=FLAGS                   Gdk debugging flags to unset
  --display=DISPLAY                      X display to use
  --screen=SCREEN                        X screen to use
  --sync                                 Make X calls synchronous
  --name=NAME                            Program name as used by the window
                                         manager
  --class=CLASS                          Program class as used by the window
                                         manager
  --gtk-debug=FLAGS                      Gtk+ debugging flags to set
  --gtk-no-debug=FLAGS                   Gtk+ debugging flags to unset
  --g-fatal-warnings                     Make all warnings fatal
  --gtk-module=MODULE                    Load an additional Gtk module

Bonobo activation Support
  --oaf-ior-fd=FD                        File descriptor to print IOR on
  --oaf-activate-iid=IID                 IID to activate
  --oaf-private                          Prevent registering of server with OAF

GNOME GConf Support

GNOME Library
  --disable-sound                        Disable sound server usage
  --enable-sound                         Enable sound server usage
  --espeaker=HOSTNAME:PORT               Host:port on which the sound server
                                         to use is running
  --version                              2.12.0.1

Session management
  --sm-client-id=ID                      Specify session management ID
  --sm-config-prefix=PREFIX              Specify prefix of saved configuration
  --sm-disable                           Disable connection to session manager

GNOME GUI Library
  --disable-crash-dialog                 Disable Crash Dialogue

t0p@lapt0p:~$


```

I looked through that, don't think there's anything I can use cron with there. Anyone see anything?

---

### Post by T. G. Cid on 2006-05-08
You can try to get cron to work with GUI apps:
[http://doc.gwos.org/index.php/Cron_GUI](http://doc.gwos.org/index.php/Cron_GUI)

Alternatively, you could grab a console-based player and use that with cron.

---

### Post by Hallavej on 2006-05-08
I think xmms-alarm is what you are looking for.

---

