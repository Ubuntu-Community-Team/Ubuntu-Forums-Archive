---
title: "Network questions"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by sabredog on 2005-12-31
How can I see my XP network PC's when opening or saving files?

I can see the network via Network Servers but cannot select a network shared drive to save to/open.

I have not installed Samba, as I am unsure how to. Would this be the reason why network links are not appearing other than in "Network Servers"?

cheers and thanks

---

### Post by Herman on 2005-12-31
Sabredog,
If your IP address for your Ubuntu machine is allowed in whatever firewall you are using in each Windows machine, your Ubuntu machine should be able to access the shared folders in any Windows machine on your LAN without installing any extra software. You were on the right track, it is in 'places', 'network servers'. It should be easy!
You don't need Samba, that's only for accessing the Ubuntu machine from Windows, but I don't know very much about that. That idea doesn't appeal to me.
If you need to find out your IP address in Ubuntu, type 'ifconfig' in a terminal, and press enter, and your IP address will be there along with lots of other stuff.
:D (Herman)

---

### Post by sabredog on 2005-12-31
Herman

Many thanks, No problems with seing the XP network. What I would like is being able to open up files within software over the network ala WindowsXP.

Eg Totem cannot play certain files that VLC can but VLC does not see the network for me to be able to open the files.

cheers and thanks

---

### Post by Herman on 2005-12-31
I tried a few ideas out here on my own LAN to see if I could help. All I can say is I don't know. The only way I know is to import the whole file through the LAN into the machine you want to open it in, but maybe someone else can help. It seems like something that should be possible. I remember trying this once already and couldn't do it. I'll let you know if I find a way. (Herman)

---

### Post by sabredog on 2005-12-31
Like you I found you had to copy the file to the local hard drive and then VLC run the file without issue.

Strange it cannot give you a browse option (along with other software packages) to browse the LAN.

cheers and thanks

---

