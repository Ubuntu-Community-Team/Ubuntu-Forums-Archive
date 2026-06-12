---
title: "file association across sytems... or not"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Repus on 2007-08-19
I’m not afraid of a little bit of scripting if that is what this requires. However, I am hoping this has a simple solution that will roll of the fingertips of Ubuntu forum members. Here is my question / scenario.

I browse with system “A”. I have bittorrent setup on system “B”. I would like to redirect browser initiated torrent downloads from system “A” to system “B”. 

Eg. On sys-A I find a torrent link and click on it. The download takes place on sys-B.

Any easy solution or should I stop bothering you kind people and start coding?

Thanks in advance

---

### Post by stijngysemans on 2007-08-19
you can save your torrents on a location on your "download system". You can program a 'watch' on that directory that automatically starts downloading the torrents in the directory.

---

### Post by Arthur Archnix on 2007-08-19
So, system 'A' is an OS, like Ubuntu or Windows, and system 'B' is a different OS, like Windows or Ubuntu? And you want to download a torrent on 'A', but have it started up by 'B'? Have I summarized your question correctly?

If so, I'm going to say no, unless system 'B' is a virtual machine running on system 'A'. I'm sure someone will correct me if I'm wrong.

Though, I could see if being possible to download a torrent from 'A' to 'B', and then have it started the next time you run 'B'. But I don't think that's what you're asking here.

EDIT: Unless, system 'B' is a server or otherwise always on OS running as a separate instance from 'A'. Then I don't think you'll have any problems. But you'll need to give more detailed info if that's the case, e.g., what are these systems, how are they connected, etc. I think that's what stijngysemans has in mind with his answer.

---

### Post by Repus on 2007-08-19
Thanks for the responses.

Arthur, yeah you got the idea. System "A" is a windows box. System "B" is an ubuntu server on a dmz. 

My original though is what Stijngy suggested (if I understand correctly).
Im inclined to download torrent files to a directory on the ubuntu-dmz server and then just have a script check the directory for new files periodically and complete the download with a BT client etc. I was just hopeing for something a little more elegant.

If you have a better idea im all ears.

---

### Post by Arthur Archnix on 2007-08-19
Thanks for the clarification. Yeah, that's possible. I'm not entirely sure how to do it, but I'll watch this thread to see if someone gives you an answer, and if not I'll see what little I can do.... :)

Best,

---

