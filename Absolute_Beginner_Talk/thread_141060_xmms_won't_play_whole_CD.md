---
title: "xmms won't play whole CD"
date: 2006-03-07
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-03-07
any ideas why not? any ideas on how to fix it? any recommendation for a lightweight audio player?

---

### Post by Pragmatist on 2006-03-08
Please give output of:
```
cat ~/.xmms/config
```

---

### Post by fuscia on 2006-03-10
[QUOTE=Pragmatist]Please give output of:
```
cat ~/.xmms/config
```[/QUOTE]

thanks for the response. here it is...


playlist_transparent=FALSE
playlist_font=-adobe-helvetica-bold-r-*-*-10-*
use_fontsets=FALSE
mainwin_use_xfont=FALSE
mainwin_font=-adobe-helvetica-medium-r-*-*-8-*
playlist_position=7
equalizer_x=20
equalizer_y=136
snap_distance=10
equalizer_visible=FALSE
equalizer_shaded=FALSE
equalizer_active=FALSE
equalizer_autoload=FALSE
easy_move=FALSE
use_eplugins=FALSE
always_on_top=FALSE
sticky=FALSE
equalizer_preamp=0
random_skin_on_play=FALSE
pause_between_songs=FALSE
pause_between_songs_time=2
mousewheel_scroll_amount=10
mouse_wheel_change=8
show_wm_decorations=FALSE
eqpreset_default_file=dir_default.preset
eqpreset_extension=preset
equalizer_band0=0
equalizer_band1=0
equalizer_band2=0
equalizer_band3=0
equalizer_band4=0
equalizer_band5=0
equalizer_band6=0
equalizer_band7=0
equalizer_band8=0
equalizer_band9=0
output_plugin=/usr/lib/xmms/Output/libALSA.so
disabled_iplugins=
url_history_length=0
skin_dirs_number=1
skin_dir0=/home/horney/.xmms/Skins
generic_title_format=%p - %t
skin=/home/horney/.xmms/Skins/Aphotic.wsz
filesel_path=/media/cdrom/

[CDDA]
device=/dev/cdrom
directory=/media/cdrom/
mixer=1
readmode=1
num_drives=1
title_override=FALSE
name_format=%p - %t
use_cddb=FALSE
cddb_server=freedb.freedb.org
cddb_protocol_level=0
use_cddb_proxy=FALSE
cddb_proxy=
cddb_proxy_port=8080
use_cdin=FALSE
cdin_server=www.cdindex.org


[OSS]
audio_device=0
mixer_device=0
buffer_size=3000
prebuffer=25
use_master=FALSE
use_alt_audio_device=FALSE
alt_audio_device=/dev/dsp
use_alt_mixer_device=FALSE
alt_mixer_device=/dev/mixer

[ALSA]
buffer_time=500
period_time=50
thread_buffer_time=3000
multi_thread=TRUE
mmap=FALSE
pcm_device=default
mixer_card=0
mixer_device=PCM
soft_volume=FALSE
volume_left=100
volume_right=100

---

### Post by Pragmatist on 2006-03-10
Any pattern to when it cuts off.  Try different CDs and see if it tends to stop playing at a similar location/track number; or, a certain number of elapsed minutes.  Or any pattern that you see.

I hear that **amaroK** is good.  I don't know if it is lightweight or not.  Do a search in Synaptic using keyword **mp3**  You might want to check out **mpg123-esd**

---

### Post by fuscia on 2006-03-10
dude, you're not going to believe what a complete retard i am. it turns out that the cds were stopping at the number the previous cd had ended at. in other words, if i played the first cd up until track8, for example, the next cd i would play would stop at track8, even if it had more tracks. what i didn't realize was that i need to reload the directory when playing a different cd. i wouldn't have figured that out had you not suggested looking for patterns. thanks very much. what a relief!

---

### Post by Chemroydal Tissue on 2006-10-03
Dang, I was hoping this would have a solution for me, but it didn't. Here's my problem: Once, I loaded a single track from the folder housing all of my music files. Since then, xmms will only play one track, even if I've loaded the entire folder (re-loading does nothing). It will play any single file - say, if I play Faith No More's Midlife Crisis, then, the next day, play Maery Lanahan's Corey - but only that one file at a time. I checked```
cat ~/.xmms/config
``` and saw nothing out of the ordinary, but I'll post it here, just to be sure (I did just finish a paper on ethics in psychological therapy):> [xmms]
allow_multiple_instances=FALSE
use_realtime=FALSE
always_show_cb=TRUE
convert_underscore=TRUE
convert_%20=TRUE
show_numbers_in_pl=TRUE
snap_windows=TRUE
save_window_positions=TRUE
dim_titlebar=TRUE
use_pl_metadata=TRUE
get_info_on_load=FALSE
get_info_on_demand=TRUE
eq_doublesize_linked=TRUE
no_playlist_advance=TRUE
sort_jump_to_file=FALSE
smooth_title_scroll=TRUE
use_backslash_as_dir_delimiter=FALSE
player_x=0
player_y=26
player_shaded=FALSE
player_visible=TRUE
shuffle=TRUE
repeat=FALSE
doublesize=FALSE
autoscroll_songname=TRUE
timer_mode=1
timer_minutes_only=FALSE
vis_type=2
analyzer_mode=0
analyzer_type=1
analyzer_peaks=TRUE
scope_mode=0
vu_mode=1
vis_refresh_rate=0
analyzer_falloff=3
peaks_falloff=1
playlist_x=0
playlist_y=142
playlist_width=300
playlist_height=232
playlist_shaded=FALSE
playlist_visible=TRUE
playlist_transparent=FALSE
playlist_font=-adobe-helvetica-bold-r-*-*-10-*
use_fontsets=FALSE
mainwin_use_xfont=FALSE
mainwin_font=-adobe-helvetica-medium-r-*-*-8-*
playlist_position=911
equalizer_x=20
equalizer_y=136
snap_distance=10
equalizer_visible=FALSE
equalizer_shaded=FALSE
equalizer_active=FALSE
equalizer_autoload=FALSE
easy_move=FALSE
use_eplugins=FALSE
always_on_top=FALSE
sticky=FALSE
equalizer_preamp=0
random_skin_on_play=FALSE
pause_between_songs=FALSE
pause_between_songs_time=2
mousewheel_scroll_amount=10
mouse_wheel_change=8
show_wm_decorations=FALSE
eqpreset_default_file=dir_default.preset
eqpreset_extension=preset
cdda_directory=/media/cdrom
equalizer_band0=0
equalizer_band1=0
equalizer_band2=0
equalizer_band3=0
equalizer_band4=0
equalizer_band5=0
equalizer_band6=0
equalizer_band7=0
equalizer_band8=0
equalizer_band9=0
skin=/usr/share/xmms/Skins/debfskin.tar.gz
output_plugin=/usr/lib/xmms/Output/libALSA.so
disabled_iplugins=
url_history_length=0
skin_dirs_number=2
skin_dir0=/home/dr10k/.xmms/Skins
skin_dir1=/usr/share/xmms/Skins
generic_title_format=%p - %t
filesel_path=/home/dr10k/Music/

[ALSA]
buffer_time=500
period_time=50
thread_buffer_time=3000
pcm_device=default
mixer_card=0
mixer_device=PCM
soft_volume=FALSE
volume_left=100
volume_right=100

Anyone have any ideas?

---

### Post by Pragmatist on 2006-10-04
> Originally Posted by **Chemroydal Tissue** ...xmms will only play one track, even if I've loaded the entire folder (re-loading does nothing)

I'm assuming your following this procedure:

1.) Open playlist editor
2.) Navigate to folder with music files
3.) Press the button labeled "add all files in directory

In that case, here are a couple of questions:

1.) Does the playlist editor display all the files in your directory?
2.) If there are multiple files showing in the playlist editor then:
    -a- Can you manually play a file lower down on the playlist editors list?

If the answers to 1, 2, and 2a. are all yes, then I'm guessing your specific problem is that xmms won't queue the next track and automatically play it.  Is that right?

Try making a small folder with a few files.  Then, just load the contents of this folder and see if xmms can play more than one track in succession.

Let us know how it all turns out.

---

### Post by Chemroydal Tissue on 2006-10-04
OK, I can't believe how stupid I am. Around the same time I played the one track, I must have needed to open a new window in either Firefox or OpenOffice, and hit ctl+n, while still using XMMS. This turned on the "No Playlist Advance" option - I should have seen it in my config,> no_playlist_advance=TRUEbut, like I said, I had just gotten through a tough paper. Sorry for the wasted time. Is there a Homer emoticon?

---

