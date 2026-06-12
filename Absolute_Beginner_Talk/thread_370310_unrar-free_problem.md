---
title: "unrar-free problem"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by william_hunter on 2007-02-25
Hail all. I have 5 files I absolutely must have for my server, but they are in .rar compression and I cannot for the life of me figure out how to get them extracted. I used synaptic to get the unrar-free program, but it won't do anything when I try to use it. Help?

---

### Post by picpak on 2007-02-25
Does

```
unrar-free -x *.rar
```

work?

---

### Post by mcduck on 2007-02-25
just right-click on the rar package and select 'Extract here' :D

If that doesn't work I'd recommend using the 'unrar-nonfree' instead of the free one.

---

### Post by william_hunter on 2007-02-25
> **mcduck said:**
> just right-click on the rar package and select 'Extract here' :D


Nope. 

Sure, pay for software...dang.

---

### Post by william_hunter on 2007-02-25
> **picpak said:**
> Does

```
unrar-free -x *.rar
```

work?

I'll try this in a few minutes.

---

### Post by Xappe on 2007-02-25
> **william_hunter said:**
> Nope. 

Sure, pay for software...dang.

unrar-nonfree is freeware, but it's not free software. You don't have to pay for it, but the source is closed (a non-free license)...

---

### Post by william_hunter on 2007-02-25
> **picpak said:**
> Does

```
unrar-free -x *.rar
```

work?

> 
whunter@whunter-desktop:/usr/local/share/nwn$ unrar-free -x nwnx_chat-0.3-linux.rar

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /usr/local/share/nwn/nwnx_chat-0.3-linux.rar

Extracting  readme                                                    Failed    
Extracting  chat/HookChat.h                                           Failed    
Extracting  chat/Makefile                                             Failed    
Extracting  chat/NWNXChat.cpp                                         Failed    
Extracting  chat/NWNXChat.h                                           Failed    
Extracting  chat/plugin-chat.cpp                                      Failed    
Extracting  chat/HookChat.cpp                                         Failed    
Extracting  nwn/chat_script.nss.sample                                Failed    
Extracting  nwn/dmb_chat.nss                                          Failed    
Extracting  nwnx_chat.so                                              Failed    
Extracting  chat/readme_src.txt                                       Failed    
11 Failed


nope. Doesnt work either. I will try the non-free version now.

---

### Post by picpak on 2007-02-25
You'll have to try

```
sudo unrar-free -x *.rar
```

---

### Post by william_hunter on 2007-02-25
That didnt work either, I tried that shortly after, but then I remembered that I enabled permissions for my username on that directory. I went ahead and got the non-free and all is now good.

Thanks folks. I am learning fast.

---

