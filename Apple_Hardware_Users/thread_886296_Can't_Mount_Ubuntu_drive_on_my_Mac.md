---
title: "Can't Mount Ubuntu drive on my Mac"
date: 2008-08-11
forum: Apple Hardware Users
---

### Post by therawski on 2008-08-11
I'm a newbie so bare with me.

I'm trying to mount my ubuntu hardy box on my mac but haven't had any luck with setting up samba or with using macfuse and sshfs.

With samba set up I connect to server, it locates it showing the workgroup, authenticates perfectly fine, shows the samba share but afterwards I get an error from my mac basically saying that it couldn't read or write to a file error -36 and fails to mount it. I don't know what's wrong

With macfuse and sshfs set up nothing happens after i hit connect, doesn't even ask me for a password it just sits there

Biggest concern is that in my mac terminal i try to ssh into my ubuntu box and it says connection refused

On my ubuntu box I have no problem with ssh into my mac and can mount it fine, I have no idea why I can't go the other way, please help, thanks

---

### Post by cyberdork33 on 2008-08-11
> **therawski said:**
> I'm trying to mount my ubuntu hardy box on my mac but haven't had any luck with setting up samba or with using macfuse and sshfs.

With samba set up I connect to server, it locates it showing the workgroup, authenticates perfectly fine, shows the samba share but afterwards I get an error from my mac basically saying that it couldn't read or write to a file error -36 and fails to mount it. I don't know what's wrong
It sounds like the share that you should have setup on your Ubuntu box is not configured correctly. You should only try to share the folder that has the files you want to access (Like your music folder).
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)

> **therawski said:**
> With macfuse and sshfs set up nothing happens after i hit connect, doesn't even ask me for a password it just sits there

Biggest concern is that in my mac terminal i try to ssh into my ubuntu box and it says connection refused

On my ubuntu box I have no problem with ssh into my mac and can mount it fine, I have no idea why I can't go the other way, please help, thanks
Did you first install opennssh-server?

---

### Post by therawski on 2008-08-11
well the SambaComprehensiveGuide didn't get me anywhere following their instructions, installing openssh-server didn't change anything except when i type sudo for anything i get:
" unable to resolve host MY COMPUTER'S NAME "
but still lets me go

on my mac when i try sshfs it still doesn't do anything and in terminal it tells me a bunch of stuff has changed, that someone is hacking my computer, and that my host key verification failed. So please help.

---

