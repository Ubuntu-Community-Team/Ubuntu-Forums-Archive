---
title: "Is updating from cd vs net possible?"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by skew on 2006-09-01
I installed Ubuntu from a cd onto one of two home computers then updated one of them over the net, which took over 14+ hours to complete on my dial-up account. (no asdl here)
  
  I now want to update ubuntu on the other system but can't afford to go through another long connection to do so. I burned all the updated (.deb) files from the first install onto a dvd but am going through dependency hell trying to install them one by one. Is there any easier way to do this? It seems ridiculas to already have all these files available and not be able to easily install them. ](*,)

 Is it possible to have *dpkg* look for a packages dependecies in the same directory as it being installed from? **ANY** help would be greatly appeciated!

---

### Post by deadgobby on 2006-09-01
I hope this will aid you.
 Go into Synaptic> Settings> then select repositories, click on the "Add CDROM" and away you go.

---

### Post by pistcivet on 2006-09-01
Copy all the .deb files to;
/var/cache/apt/archives

Then you can install with synaptic (or apt-get I suppose).
You'll still have to update the channels.

---

### Post by Dr. Nick on 2006-09-01
sudo dpkg -i *.deb 

that will install all .deb files in the directory, it will not download new dependencies though if needed. thier have been other methods described on here if that doesnt work

---

### Post by skew on 2006-09-01
> **Dr. Nick said:**
> sudo dpkg -i *.deb 

that will install all .deb files in the directory, it will not download new dependencies though if needed. thier have been other methods described on here if that doesnt work

Thanks I'll give that a try it.

---

