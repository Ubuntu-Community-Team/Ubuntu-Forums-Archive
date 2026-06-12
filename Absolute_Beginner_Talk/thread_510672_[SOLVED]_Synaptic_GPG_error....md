---
title: "[SOLVED] Synaptic GPG error..."
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by 3ark on 2007-07-26
Ok so what I was doing was trying to get dvd playback and I went to Synaptic to get some packages for that. I enabled the multiverse and universe repositories but upon reloading I got this error 

W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

:-k Yeah, it never did that before and I don't know what to do now. The only thing I've done recently was install picasa. Any help is greatly appreciated.

---

### Post by ggaaron on 2007-07-26
You are sure that you have only the official ubuntu repositories? Maybe you added a repository and forgot to do the GPG step? Or more probably you have a wrong line somewhere there with dl.google.com as a repository?

---

### Post by 3ark on 2007-07-26
Well actually I'm still pretty new to the linux game so I'm not really sure of anything unfortunately. I dont know what the GPG step is exactly, nor do I know how to find a wrong line or fix it. I'm probably not much help in explaining this. :confused:

Edit: I was just playing in Synaptic, I found a line saying the google part, and unchecked it, I reloaded and didnt get the error this time, should I be good to go now, or is there more?

---

### Post by Seisen on 2007-07-26
Put this in the terminal to get the key for it so you can use it.

```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
```

---

### Post by ggaaron on 2007-07-26
Example:
[http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

If you had missed the second line then a GPG error would rise, I'm not a pro in it either, I just know that it happened to me when I only added a repository, oh I see that there is a solution posted already.

---

### Post by 3ark on 2007-07-26
Tried that and this came up:

gpg: no writable keyring found: eof
gpg: error reading `-': general error
gpg: import from `-' failed: general error

---

### Post by Seisen on 2007-07-26
Try it again sometimes it doesn't work the first time or put sudo in front of the command.

---

### Post by 3ark on 2007-07-26
I think I got it. Everything seems to be functioning as normal. Thanks! Without you guys on this forum it would be way harder to get things set up as your learning the new OS. :popcorn:

---

