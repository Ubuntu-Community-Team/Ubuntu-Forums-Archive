---
title: "Mintmenu"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by arijarot on 2007-06-17
I followed this [post]("http://ubuntuforums.org/showthread.php?t=387315&highlight=mintmenu&page=3") and added linuxmint to the repository list. When I went to install mintmenu in synaptic, it told me that (see attachment). 
What does this mean?

---

### Post by skymera on 2007-06-17
i think it means its unsupported software.
runs on ubuntu, but you cant get support.

i think

---

### Post by Happy_Man on 2007-06-17
It just means you don't have a GPG key, Ubuntu can't confirm it's not some sort of computer-crashing ****, and is just trying to warn you of the above issues. If you trust them, click ok.

---

### Post by Golyadkin on 2007-06-17
It is a security warning. If you install something from the official Ubuntu servers, they will vouch for the integrity and authenticity of the installer you download.
The repository you download from, is not an official Ubuntu server. Therefore, it is up to you to trust the owner of that repository to make sure there are no malicious installers on the repository. 
For instance: I can setup a repository very easily, and say I am hosting a super deluxe ATi driver for Linux on it, even better than the Catalysts. Now I can simply replace that driver with a virus program. People will come to my repository, install the package which executes a script and deletes every file in your homedir. 
This is a risk, even though it is far fetched. To protect you from this, Ubuntu warns you when a server is not official. 99.9% of the time there are no malicious packages on these unofficial repositories, but it is possible. Therefore, Ubuntu warns you so you can decide yourself if you trust the repository.

There, a lot of text but I hope it makes it clear for you.

---

### Post by arijarot on 2007-06-17
well, should I trust linux mint? why wouldn't they use a key / give a key?

---

### Post by Golyadkin on 2007-06-17
It is up to you to decide if you trust them. My own feeling with this is that you can trust them, based on the fact that I have seen other people install mint from that same repository, and they have not complained about it having malicious packages on it.

---

### Post by zvacet on 2007-06-17
Mint is distro based on Ubuntu,so I think you can trust them.

---

