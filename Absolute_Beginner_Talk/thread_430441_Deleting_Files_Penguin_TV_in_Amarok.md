---
title: "Deleting Files: Penguin TV in Amarok"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-05-02
I was running Icepodder (podcast catcher)on Ubuntu but when I upgraded to Feisty it wouldn't load. So I went looking and installed PenguinTV  which is quite good although I have to load it every time through a Terminal prompt 
> sudo PenguinTV
and often have to leave Terminal open because every time I close Terminal Penguin TV exits.
But now when playing my fMp3 podcast files in Amarok I cannot delete them from that window --unlike I could with the  audio file archive created by Icepodder (or Ipodder before that).

My file line is :
> /home/ratbagradio/.penguintv/media/

and I want to change my permissions so i can delete direct without having to chase the folder and do it manually. I've played around with > Administration/Users and Groups but I cannot get the power I'm after. There must be a way to empower me to delete direct from with Amarok?

I'd shift the folder to somewhere that may allow me to do direct delete by PenguinTV won;t offer that preference option.

I'd prefer to use IcePodder (because it archives by program and not by date)but then I make do  and really PenguinTV isn''t bad even for audio. So I can learn to love it. It has other plusses too. Deleting is not one of them.

My Penguin TV load is: (codes deleted to allow me to post to this forum)

.............> .:~$ sudo PenguinTV
using pynotify notifications
Unable to find definition '...
 function snd_func_refer returned error: No such file or directory
 Args evaluate error: No such file or directory

 Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
initializing mozilla in /usr/lib/firefox
initializing ajax server
 Unable to find definition 'defaults.pcm.dmix_format'
 function snd_func_refer returned error: No such file or directory
) Args evaluate error: No such file or directory
 Unknown PCM dmix:I82801BAICH2
/usr/lib/python2.5/site-packages/penguintv/MainWindow.py:337: GtkWarning: gtk_window_resize: assertion `width > 0' failed
  self.app_window.resize(w,h)
:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
(snd_config_expand) Args evaluate error: No such file or directory
:(snd_pcm_open_noupdate) Unknown PCM dmix:I82801BAICH2
no gstreamer player to get
:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
:(snd_config_expand) Args evaluate error: No such file or directory
:(snd_pcm_open_noupdate) Unknown PCM dmix:I82801BAICH2
:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
(snd_config_expand) Args evaluate error: No such file or directory
(snd_pcm_open_noupdate) Unknown PCM dmix:I82801BAICH2





---

### Post by carl0ski on 2007-05-02
try 
sudo tvpenguin&


the & sends the program to the background and will allow you to close the terminal safely

---

### Post by ratbagradio on 2007-05-02
Thanks that works: I can close Terminal and keep penguinTV running. Now all I have to do is solve my"delete" issue

---

