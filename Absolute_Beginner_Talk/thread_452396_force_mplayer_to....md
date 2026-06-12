---
title: "force mplayer to..."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-05-23
how can i force mplayer to automatically open videos double-sized? to loop videos? i didn't find these in settings menu :(

---

### Post by ggaaron on 2007-05-23
CONFIGURATION FILES
       You can put all of the options in configuration files which will be read every time MPlayer/MEncoder is run.  The system-wide config-
       uration  file  'mplayer.conf' is in your configuration directory (e.g. /etc/mplayer or /usr/local/etc/mplayer), the user specific one
       is '~/.mplayer/config'.  The configuration file for MEncoder is 'mencoder.conf' in your configuration directory (e.g. /etc/mplayer or
       /usr/local/etc/mplayer),  the user specific one is '~/.mplayer/mencoder.conf.  User specific options override system-wide options and
       options given on the command line override either.  The syntax of the configuration files is 'option=<value>', everything after a '#'
       is  considered  a comment.  Options that work without values can be enabled by setting them to 'yes' or '1' or 'true' and disabled by
       setting them to 'no' or '0' or 'false'.  Even suboptions can be specified in this way.

       You can also write file-specific configuration files.  If you wish to have a configuration file for a file called 'movie.avi', create
       a  file  named  'movie.avi.conf'  with the file-specific options in it and put it in ~/.mplayer/.  You can also put the configuration
       file in the same directory as the file to be played, as long as you give the -use-filedir-conf option (either on the command line  or
       in your global config file).

Your options probably will me somewhere there, or they surely will be in man mplayer.

---

