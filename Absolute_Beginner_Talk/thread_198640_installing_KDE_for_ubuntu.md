---
title: "installing KDE for ubuntu"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by covetous_kid on 2006-06-17
Hi,

I currently have ubuntu 5.04 installed on my computer, and I want to install KDE for it. I have spent a lot of time trying to do this by looking at forums and manuals and what not, but it still doesn't work. 

Here's what I've done: When I try apt-get install kubuntu-desktop, it always says "Couldn't find package kubuntu-desktop". I've tried searching for it in Synaptic Package Manager and couldn't find it there either. Even when I downloaded the Kubuntu install CD and did apt-cdrom add, it didn't make any difference. (All commands were preceded with sudo of course.) I also have a solid internet connection, and I have done apt-get update numerous times at various stages, although it never seems to do anything besides read the package list.

Can someone tell me what's the problem and what I can do to fix us? Any help would be appreciated.  Thanks in advance!

---

### Post by PriceChild on 2006-06-17
Do an ```
apt-get update
``` before trying to install kubuntu-desktop.

If this doesn't work then you may want to try posting your sources list here...

(/etc/apt/sources.list)

Pricey

---

### Post by covetous_kid on 2006-06-17
[QUOTE=PriceChild]

(/etc/apt/sources.list)

[/QUOTE]

Aha! That's why... all my sources are commented out by default. Thanks!

---

