---
title: "folder and content permision"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by sabitha on 2006-08-26
is there any way to make my folder and its content can,t be copy by user but user can read/or play on xmms. the folder is mp3 folder i need that for my internet cafe because i always got my folder blow away/missing maybe theres someone deleted the folder and empty the trash.:cry:

---

### Post by Skia_42 on 2006-08-26
The only thing I can think off is make the file readable by root and give xmms root permissions. I do not have much experience programming so I do not know how to do the xmms end of it. Changing the file owner and permissions is the easy part, just use > chown and > chmod.

---

### Post by bodhi.zazen on 2006-08-26
Is your problem one of copy protection or deletion?

If only deletion , assume a directory "xmms" which contains your music.

Make a new group also named "xmms"
sudo chown root:xmms xmms
sudo shmod 750 xmms

All (music) files in the directory xmms need to be owned by root:xmms, with permissions 640

sudo chown -R root:xmms xmms/*
sudo chmod -R 640 xmms/*

Now users in the xmms group will have access to, but not write permissions for, the music files.

I do not know how to keep them from copying the files, but where would they copy to? Do not give users a place to copy to (home, floppy, USB, etc) and you should be fine. No need to give users a large space in /home/user for writing is there? Set a quota for /home/user.

Make a group say USB with access to USB/Floppy/other storage media. Do not allow users to belong to both the USB and xmms group at the same time.

---

### Post by sabitha on 2006-08-26
> Do not give users a place to copy to (home, floppy, USB, etc) and you should be fine.
if i dont give user to copy how about if they download something important from internet to they use at home. i just want my mp3 folder(my_music) safe from delete

---

### Post by bodhi.zazen on 2006-08-26
I see. If you are not worried about copy protection, the permissions above should work for preventing deletion. You may not need an xmms group.

If you need more help let us know.

---

### Post by sabitha on 2006-08-26
so what ive got to do now the folder is /home/client/music
plz tell me detail on command line

---

### Post by bodhi.zazen on 2006-08-26
I would do this:
(If yo have not done so, make a group "client")

```
sudo chown -R root:client /home/client/music
sudo chmod 655 /home/client/music
sudo -R chmod 644 /home/client/music/*
```

All files are now owned by Root and only root can add/change/delete.

If you want to restrict access to the music to only root and members of the client group change the 3rd digit in chmod to 0 (ie 650 and 640).

---

### Post by sabitha on 2006-08-27
> sudo -R chmod 644 /home/client/music/*
i've got this for the last :
admin@admin-raungnet:~$ sudo -R chmod 644 /home/admin/music/*
sudo: illegal option `-R'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

but its ok even user that not right (for the last command) now my folder safe. thanks for the help thats very helpful for my internet cafe. now :D
for the last question can u make user can't copy too?

---

### Post by bodhi.zazen on 2006-08-27
> **sabitha said:**
> i've got this for the last :
admin@admin-raungnet:~$ sudo -R chmod 644 /home/admin/music/*
sudo: illegal option `-R'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }

but its ok even user that not right (for the last command) now my folder safe. thanks for the help thats very helpful for my internet cafe. now :D
for the last question can u make user can't copy too?

There is s small typo, the "R" comes AFTER chmod like this:
```
sudo chmod -R 644 /home/admin/music/*
```

I am not sure what type of copy protection your are asking about? If you do not want your useres to copy the music files, perhaps stream the music (AKA Stream your music).

See [http://www.oreillynet.com/xml/blog/2004/12/streaming_itunes_from_ubuntu.html](http://www.oreillynet.com/xml/blog/2004/12/streaming_itunes_from_ubuntu.html)

---

