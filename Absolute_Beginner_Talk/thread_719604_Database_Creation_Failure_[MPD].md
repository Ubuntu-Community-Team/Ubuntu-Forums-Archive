---
title: "Database Creation Failure [MPD]"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by filam on 2008-03-09
I tried to install MPD/MPC and get them functioning. I continually ran into a problem I could not find a solution for online. After installing MPD/MPC I attempted to create a database and I get the following message:
> cannot open music_directory "/home/filam/music/" (config line 8 ): No such file or directory
I have used a variety of different variables to define the music_directory, but they continually fail. Any ideas?

**.mpdconf**
```
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/home/filam/music/"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
pid_file		"/var/run/mpd/pid"
################################################################

######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            ""
#
# The address and port to listen on.
#
bind_to_address                 "127.0.0.1"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################
```
**etc/mpd.conf**
```
# An example configuration file for MPD
# See the mpd.conf man page for a more detailed description of each parameter.

######################## REQUIRED PATHS ########################
# You can put symlinks in here, if you like. Make sure that
# the user that mpd runs as (see the 'user' config parameter)
# can read the files in this directory.
music_directory		"/var/lib/mpd/music"
playlist_directory	"/var/lib/mpd/playlists"
db_file			"/var/lib/mpd/tag_cache"
log_file		"/var/log/mpd/mpd.log"
error_file		"/var/log/mpd/errors.log"
pid_file		"/var/run/mpd/pid"
################################################################


######################## OPTIONAL PATHS ########################
#
# If specified, MPD will save its current state (playlist,
# current song, playing/paused, etc.) at exit.  This will be
# used to restore the session the next time it is run.
#
state_file		"/var/lib/mpd/state"
#
################################################################


######################## DAEMON OPTIONS ########################
#
# If started as root, MPD will drop root privileges and run as
# this user instead.  Otherwise, MPD will run as the user it was
# started by.  If left unspecified, MPD will not drop root
# privileges at all (not recommended).
#
user                            "mpd"
#
# The address and port to listen on.
#
bind_to_address                 "localhost"
#port                            "6600"
#
# Controls the amount of information that is logged.  Can be
# "default", "secure", or "verbose".
#
#log_level                       "default"
#
################################################################


########################## PERMISSIONS #########################
#
# MPD can require that users specify a password before using it.
# You may specify one ore more here, along with what users who
# log in with that password are allowed to do.
#
#password                        "password@read,add,control,admin"
#
# Specifies what permissions a user who has not logged in with a
# password has.  By default, all users have full access to MPD
# if no password is specified above, or no access if one or
# more passwords are specified.
#
#default_permissions             "read,add,control,admin"
#
################################################################


########################## AUDIO OUTPUT ########################
#
# MPD supports many audio output types, as well as playing
# through multiple audio outputs at the same time.  You can
# specify one or more here.  If you don't specify any, MPD will
# automatically scan for a usable audio output.
#
# See <http://mpd.wikia.com/wiki/Configuration#Audio_Outputs>
# for examples of other audio outputs.
#
# An example of an ALSA output:
#
#audio_output {
#        type                    "alsa"
#        name                    "My ALSA Device"
#        device                  "hw:0,0"     # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of an OSS output:
#
#audio_output {
#        type                    "oss"
#        name                    "My OSS Device"
#        device                  "/dev/dsp"   # optional
#        format                  "44100:16:2" # optional
#}
#
# An example of a shout output (for streaming to Icecast):
#
#audio_output {
#        type                    "shout"
#        name                    "My Shout Stream"
#        host                    "localhost"
#        port                    "8000"
#        mount                   "/mpd.ogg"
#        password                "hackme"
#        quality                 "5.0"
#        bitrate                 "128"
#        format                  "44100:16:1"
#        user                    "source"                # optional
#        description             "My Stream Description" # optional
#        genre                   "jazz"                  # optional
#        public                  "no"                    # optional
#}
#
# Force all decoded audio to be converted to this format before
# being passed to the audio outputs.
#
#audio_output_format             "44100:16:2"
#
################################################################


############################# MIXER ############################
#
# MPD needs to know what mixer settings to change when you
# adjust the volume.  If you don't specify one here, MPD will
# pick one based on which ones it was compiled with support for.
#
# An example for controlling an ALSA mixer:
#
#mixer_type                      "alsa"
#mixer_device                    "default"
#mixer_control                   "PCM"
#
# An example for controlling an OSS mixer:
#
#mixer_type                      "oss"
#mixer_device                    "/dev/mixer"
#mixer_control                   "PCM"
#
# If you want MPD to adjust the volume of audio sent to the
# audio outputs, you can tell it to use the software mixer:
#
#mixer_type                      "software"
#
################################################################


######################### NORMALIZATION ########################
#
# Specifies the type of ReplayGain to use.  Can be "album" or
# "track".  ReplayGain will not be used if not specified.  See
# <http://www.replaygain.org> for more details.
#
#replaygain                      "album"
#
# Sets the pre-amp used for files that have ReplayGain tags.
#
#replaygain_preamp               "0"
#
# Enable on the fly volume normalization.  This will cause the
# volume of all songs played to be adjusted so that they sound
# as though they are of equal loudness.
#
#volume_normalization            "no"
#
################################################################


########################### BUFFERING ##########################
#
# The size of the buffer containing decoded audio.  You probably
# shouldn't change this.
#
#audio_buffer_size               "2048"
#
# How much of the buffer to fill before beginning to play.
#
#buffer_before_play              "0%"
#
# Similar options for the HTTP stream buffer.  If you hear
# skipping while playing HTTP streams, you may wish to increase
# these.
#
#http_buffer_size                "128"
#http_prebuffer_size             "25%"
#
################################################################


########################### HTTP PROXY #########################
#
# Specifies the HTTP proxy to use for playing HTTP streams.
#
#http_proxy_host                 "proxy.isp.com"
#http_proxy_port                 "8080"
#http_proxy_user                 "user"
#http_proxy_password             "password"
#
################################################################


############################# LIMITS ###########################
#
# These are various limits to prevent MPD from using too many
# resources.  You should only change them if they start
# restricting your usage of MPD.
#
#connection_timeout              "60"
#max_connections                 "5"
#max_playlist_length             "16384"
#max_command_list_size           "2048"
#max_output_buffer_size          "8192"
#
################################################################


###################### CHARACTER ENCODINGS #####################
#
# If file or directory names do not display correctly, then you
# may need to change this.  In most cases it should be either
# "ISO-8859-1" or "UTF-8".  You must recreate your database
# after changing this (use mpd --create-db).
#
filesystem_charset              "UTF-8"
#
# The encoding that ID3v1 tags should be converted from.
#
id3v1_encoding                  "UTF-8"
#
################################################################


######################### OTHER OPTIONS ########################
#
# The metadata types MPD will recognize.
#
#metadata_to_use                  "artist,album,title,track,name,genre,date,composer,performer,disc"
#
# Enable this if you wish to use your MPD created playlists in
# other music players.
#
#save_absolute_paths_in_playlists "no"
#
################################################################
```

---

### Post by chochem on 2008-03-10
I'm not sure about how to interpret your error message (I take it you're yelling at the screen 'It's there! Take a look, you [stream of obscenities]" ? :) ) but a few things come to mind
1) Since the database file is to be created in a directory owned by root, I take it you are using sudo with the 'mpd --create-db' command?
2) I seem to recall it being repeated like a mantra: 'sudo killall mpd' before you run the sudo 'mpd --create-db'. Well it seemed to help some people.
3) I had a lot of problems changing these settings too. So in the end I didn't. Symbolic links worked like a charm for me. Why not try:
```
sudo ln -s /home/filam/music /var/lib/mpd/music
sudo ln -s /home/filam/music/playlists /var/lib/mpd/playlists

```
on a fresh install?

And congrats on choosing MPD :) I only gave up on wine-foobar when I found this little gem. Hope you get i to work.

---

### Post by filam on 2008-03-10
Haha. Thanks for the reply. I am entirely confused. If it was a problem with printer drivers, x-org or any other of the essentials I'm sure I would be, but this is more like very tasty and warm apple crumble pie with vanilla ice cream, so I'm willing to wait.
I have tried using root and symbolic links (within the .mpdconf file) to get it to work, but to little success. I installed mpd a while ago, and something may have gone wrong in the mean time.
My system is actually rather bloated, which will prompt me to do a fresh install next week. I'll probably try again on a clean slate.
Thank you for the help,

---

### Post by chochem on 2008-03-10
> **filam said:**
> Haha. Thanks for the reply. I am entirely confused. If it was a problem with printer drivers, x-org or any other of the essentials I'm sure I would be, but this is more like very tasty and warm apple crumble pie with vanilla ice cream, so I'm willing to wait.

Okay, now you just gut me hungry for some of that... :D

That sounds odd... Would it still be the same error message if settings were left to their defaults (i.e. dir isn't there)? Or something else? Anyway, sounds like a good idea to start over. If you want to, you could try testing the whole thing before you start muckng about by (sudo) copying a single mp3 file into the default 'music' directory and then do the create-db thing. If that workd then just take it from there, step by step, adding symbolic links etc.

Good luck :)

---

