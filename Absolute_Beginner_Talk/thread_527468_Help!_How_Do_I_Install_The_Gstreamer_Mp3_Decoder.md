---
title: "Help! How Do I Install The Gstreamer Mp3 Decoder???"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by treyping on 2007-08-16
Well, i installed the new rhythmbox so i can play from my mp3 and that part works. The thing that i need help with is that when i tried to copy all my media files from my mp3  to my libraray it said i couldnt because i needed the g streamer plug in
i downloaded it but i have no idea how to install it. i extracted it to my desktop but i think i have to use commands and stuff with the terminal right? please tell me how to install this!!!! thanks.

---

### Post by hyper_ch on 2007-08-16
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by amazingtaters on 2007-08-16
open up the terminal and type in

```
sudo apt-get install gstream*
```

---

### Post by chrisN_uk on 2007-08-16
I'm sure this is already covered in the forum but never mind. 

Ubuntu has a tool for installing programs called atp.  So you can type

```

sudo aptitude install package

```

where package is what you want to install.  Using this you don't need to download files, it will do it automatically. You can use 
```
sudo aptitude search
``` to search for packages too. There's loads of info on these forums already so I'd recommend taking a look at other posts. 

You could also go Applications -> Add/Remove Programs and search for Gstraemer.

---

