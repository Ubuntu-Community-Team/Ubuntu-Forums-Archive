---
title: "[SOLVED] Wireless connection problem"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by satterle on 2008-03-17
I'm having troubles with wireless networking.

I recently upgraded to a Linksys WRT100 wireless router. I upgraded because I was not getting a good connection to the old wireless router (4 years old Linksys).

I have two issues:

1. I'm still not getting great connection (I'm 5 feet from the router). The toolbar indicator oscillates between one bar and four bars and periodically the connection drops. Makes no sense to me. Right now, when I click on the toolbar indicator, the connection widget shows the signal strength at 100% but the indicator is at 70%.

2. I have not been able to connect using either WEP-128 or WPA-Personal. The setup application for the WRT100 sets the encryption key automatically, so I don't know what the passphrase is. When I enter the encryption key, the connection is refused. So I'm connected with no security set.

An old Averatec 3360 model laptop.
Intel wifi -- 4300 series I believe (and that's another question -- I know where to find this information on XP. Where on Ubuntu?)
Ubuntu Gutsy

Amos

---

### Post by TeoBigusGeekus on 2008-03-17
[http://ubuntuforums.org/showthread.php?t=705391]("http://ubuntuforums.org/showthread.php?t=705391")

---

### Post by Atomic Dog on 2008-03-17
Change the channel on the router.  Try 1 or 11 instead.  I use netstumbler to searchout the clearest air and then set the channel on that freq, but its a windows app so using it in Ubuntu is not an option.

The security part... just look through a few faq's.  You'll find something there that should help you through it.

---

### Post by dca on 2008-03-17
Posting the output of* lspci* at CLI will tell us what Intel card you have.
 
OR
 
...if it's Ubuntu Gnome you can access from 'System -> Preferences -> Hardware Information' option..

---

### Post by satterle on 2008-03-17
PRO/Wireless 2200BG Network Connection, if that's a help. (so it's NOT the 4300 series. So much for memory!)

And two etiquette questions. How do I mark a thread SOLVED? I also noticed that there's a metric for how many THANKS -- how do I do that except by saying "Thanks"?

---

### Post by dca on 2008-03-17
Years ago I had a Dell laptop that had an IPW2200 and it ran Dapper (6.06LTS)...  The only thing I needed for the laptop was this if I remember correctly...

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)
 
...somebody still using the card may want to chime in to see if that package is still available in 7.10 or if it's even used anymore...

---

### Post by forrestcupp on 2008-03-17
To set the wireless security on your router, you will need to hard connect to it with a network cable.  Then you can open Firefox and type the router's address in the address bar, and it should bring up the router's settings.  Somewhere in there will be the settings for wireless security, and you can change the code to be whatever you want.

The weak signal may be from your wireless card instead of the router.


About the 'Thanks' thing, there is a button that looks like a ribbon to the left of the Quote button on each post except yours.  You can't thank yourself.

About the 'Solved' thing.  You can only mark a thread solved if you started it.  There should be a button for that.

---

### Post by satterle on 2008-03-17
I installed wicd and deleted the gnome network manager. this indeed seems to have increased the throughput.

Logged into the router and played with the encryption settings, but still can't get it to work.

Appreciate the link to the intel driver, but that's more than I can handle right now. noob burnout.

Not that concerned about encryption rather than protecting my bandwidth, so next step is to try MAC restrictions.

Thanks to all for such quick feedback.

---

