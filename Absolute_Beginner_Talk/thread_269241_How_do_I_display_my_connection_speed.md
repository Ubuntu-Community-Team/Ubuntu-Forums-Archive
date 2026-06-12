---
title: "How do I display my connection speed?"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by ahilde on 2006-10-01
I use a dial-up connection.  Frequently is connects at very slow speeds and I have to dial a new connection.  In Mozilla with Windows I see the speed at connection time.  How can I do this in Ubuntu?
Thanks

---

### Post by editrix on 2006-10-01
KPPP will do this, and I think you can use it in Gnome. There's also something like Gnome-ppp (not sure of the name) which I think will do the same thing.

---

### Post by _duncan_ on 2006-10-02
Yes, gnome-ppp will show download and upload speeds at KBytes/sec. Thus, my normal download speed is in the range 4.8 - 5.3 kBytes/sec.

Most Windows-XP users will have to get used to a change in terminology though, since the system tray icon of xp displays connection speeds in terms of kBits/sec. My connect speed is in the 46 - 48 kBits/sec range in XP.

A word of caution: Some dial-up users were unable to connect using gnome-ppp, even if wvdial or pppconfig works for them. An alternative is to add the network monitor applet to your desktop panel. Just right-click on the panel, a menu will pop-up, choose "Add to panel", and look for 'Network Monitor'. Then dial-out using whatever method suits your system.

---

### Post by ahilde on 2006-10-02
Thanks for the suggestions.  I put the system monitor up, but it just bits being sent and received, not the speed.  Do I need to configure it somehow?  Would love to just have a number showing somewhere.

---

### Post by ahilde on 2006-10-02
I meant network monitor

---

### Post by _duncan_ on 2006-10-02
Sorry about the mix-up. I disabled all my network-related applets ever since I got gnome-ppp working. But after reading your post I enabled them again and you are right. Now I remember how I used to do it.

I also had modem monitor added to the system tray, which gives total amount of time connected. So I used this info together with those of network monitor to get an approximation of my connection speed. It's fairly accurate if you're downloading stuff, but if your activity is mainly browsing/surfing, it's very far from your actual connection speed.

The better solution really is to use gnome-ppp. I never tried kppp here in Ubuntu so I don't know how it works.

Tell you what, why don't you try installing gnome-ppp using synaptic package manager? If you can't get it to work, come back here and I'll try to help you sort it out.

---

### Post by ahilde on 2006-10-04
Thanks for being willing to help. 
So far I haven't been able to find Gnome-ppp on my system.  It may come with the 179 updates I am downloading a bit at a time. 
Of course it's frustrating downloading when I'm not sure of the speed.](*,)

---

### Post by Ayman on 2006-10-04
Hi ahilde,

gnome-ppp is in the "universe" repository, to enable it, follow [these intructions](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_apt-get_the_easy_way_.28Synaptic.29). After that, you should be able to find gnome-ppp in Synaptic.

---

### Post by fragos on 2006-10-04
Firefox has a "Bandwidth Meter" extension that will test the bandwidth up and down for you.  There are many factors that impact utilized bandwith.  Google has fast pipes so the performance is ususally as good as gets for you.  The extension will show you the bandwith your network can deliver to you at that point in time.

---

### Post by andiii on 2006-10-04
Conky can do that as well

---

### Post by _duncan_ on 2006-10-05
> Thanks for being willing to help.
So far I haven't been able to find Gnome-ppp on my system. It may come with the 179 updates I am downloading a bit at a time.
Of course it's frustrating downloading when I'm not sure of the speed.

I'm not sure about this, but doesn't Synaptic show the download speed while you're updating? If I remember correctly it's just below the progress bar, expressed in bytes per second.

BTW, the link Ayman provided is pretty good.

---

