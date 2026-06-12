---
title: "MP3 problems, tar.gz, Kazaa equivalent"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by raincloudboy0 on 2005-10-05
Right. These are three complete idiot questions, so please bear with me.

1) I can't get mp3s to work on here. What do I have to do so that Ubuntu will play them?

2) How do you extract and install .tar.gz files? I did it before but I don't remember how. D'oh.

3) Is there any Linux equivalent of Kazaa for music downloading?

Thanks.

---

### Post by matthewv on 2005-10-05
[QUOTE=raincloudboy0]Right. These are three complete idiot questions, so please bear with me.
1) I can't get mp3s to work on here. What do I have to do so that Ubuntu will play them?
[/QUOTE]
I would download the codec package from [www.mplayerhq.hu](www.mplayerhq.hu) and extract it to /usr/lib/win32 (see below) and then install totem-xine. It worked for me!
> 
2) How do you extract and install .tar.gz files? I did it before but I don't remember how. D'oh.

Double clicking on the file should open file-roller for extracting. In the commandline i think its gunzip to extract the gz and then tar -xvf to extract the tarball. I your installing (from source) extract it with these commands, then
```

cd <folder created>
./configure
make
sudo checkinstall

```
> 
3) Is there any Linux equivalent of Kazaa for music downloading?
Thanks.

Sorry, no idea.. never done any of that

---

### Post by loupy on 2005-10-05
For a kazaa equivalent install "gtk-gnutella" from the synaptic package manager.  Make sure you have the universe and multiverse (I'm not sure which one it is in) added to your repositories in /etc/apt/sources.list

---

### Post by raincloudboy0 on 2005-10-05
> extract it to /usr/lib/win32 

Should there already be a directory by that name? If so, I have a problem because there isn't one. 

Thanks for the advice on gtk-gnutella. That seems fine.

---

### Post by raincloudboy0 on 2005-10-05
Never mind about the win32 thing, I think I'm getting it sorted out.

---

