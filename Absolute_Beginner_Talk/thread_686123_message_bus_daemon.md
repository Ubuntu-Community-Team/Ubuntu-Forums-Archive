---
title: "message bus daemon"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by greendragonfire on 2008-02-02
When I turn my computer off, and the black screen comes up, with the text, at the bottom it says:
NetworkManager:nm_dbus_signal_device_status_change: assertion 'cb_data->data->dbus_connection' failed
NetworkManager:<Warn> nm_dbus_init():nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

So... what do I do to fix whatever it is that's wrong?

---

### Post by nat6138 on 2008-02-02
I have the same problem. but I don't think it does anything harmful, cause' I've had the error message for along time, and it hasn't done anything bad yet.

---

### Post by greendragonfire on 2008-02-02
Yeah, I've had this message pop up for as long as I've had this computer... and I don't know if it's caused any problems, I just figured I should fix it _before_ I notice something amiss.

---

### Post by vjkeito on 2008-04-29
bump

---

### Post by agaudio on 2008-05-02
Anyone ever solve this? It started happening to me after I upgraded to Hardy.

---

### Post by GavinZac on 2008-05-02
Whats happening is that the first time it tries, your network manager isn't getting a connection. It tries to change the displayed status of the connection by updating whatever displays the status using dbus, the 'daemon' for communication between programs. However, dbus (and the GUI which would be using it) hasn't started yet.

I don't know why NM would start before the dbus but there must be some logic to it, and some cause, since it doesn't happen to me.

However, if your NM works when everything has loaded then I guess its just a purely cosmetic annoyance.

---

### Post by agaudio on 2008-05-02
Why is the network manager trying to get a connection during shutdown? Though I guess it makes sense that there is a problem, because just before the error regarding dbus. there is an output to the screen "Deactivating device eth0".

---

### Post by GavinZac on 2008-05-02
> **agaudio said:**
> Why is the network manager trying to get a connection during shutdown? Though I guess it makes sense that there is a problem, because just before the error regarding dbus. there is an output to the screen "Deactivating device eth0".

Oh, this isn't actually happening at shutdown time, its just recalling the list of boot/reboot messages it had at the start. I think; I get similar messages that occurred at boot time when I go to shutdown.

---

### Post by caleechee on 2008-05-02
With Hardy, I see this problem in situations where my IBM Thinkpad T60p laptop is connected to a dock and I'm shutting down. The shutdown process actually hangs (computer doesn't shutdown completely). My current workaround is to disable network connections in Network Manager prior to shutdown, which seems to resolve the issue and enable a successful system shutdown.

---

### Post by bastos77 on 2008-05-20
Same with me under Hardy. At shutdown my Computer is very slow and is not turning off at the end. Then after seral minutes the message "make sure that the message bus deamon is running" pops up. Then I can hit the off/on button and computer shuts off...

---

### Post by Bruce M. on 2008-07-23
This has been a problem with me since Ubuntu 6.06 right through to 8.04.

I find it hard to believe that people would say, "Oh not a problem, it doesn't hurt anything." Which very well may be the case, it doesn't hurt anything ... 

[COLOR="Red"][SIZE="5"]**[CENTER]BUT[/CENTER]**[/SIZE][/COLOR]

The system is saying there is an error that needs to be addressed.

Someone out there must have an answer. Or does absolutely every version of Ubuntu; Xfce, Gnome, Kde, Studio or Edubuntu have the same problem and "everyone" simply ignores it because:

[CENTER]**It doesn't hurt anything!**[/CENTER]

despite the fact the system is showing an error?

I hope we see an answer here.

Have a nice day
Bruce

---

### Post by mailtwogopal on 2008-07-23
hi all,

 i agree with bruce as i am also having exactly the same problem while i shutting down my box. But the process looks fast and not very slow during shut down. But this issue needs to be resolved. 

I am sure that atleast one from this forum will definitely have answer for this issue. Please help us guys.

---

### Post by Bruce M. on 2008-07-23
So far there are nine of us here with the same problem. So I created a thread in General Help: [Errors with message bus daemon]("http://ubuntuforums.org/showthread.php?p=5444742#post5444742") to see if I can pull in some help from that area.

The plea for help was on behalf of all of us, by name. Please don't shoot me for mentioning your name in that post.

"I fell into a burnin' ring of fire ... " :guitar:

Gotta love Johnny Cash. :lolflag:
"X"ing fingers.
Bruce

---

### Post by Amarsingh0793 on 2008-07-23
Hi Guys! I'm just wondering, are you having a "Failed to Initialze HAL" Error message at login? If so, I haveposted a solution here: [http://ubuntuforums.org/showthread.php?t=23291](http://ubuntuforums.org/showthread.php?t=23291)

HAL is related to dbus somehow, I think...

Hope this helps you guys :)

---

### Post by wjwh on 2008-07-23
> **Bruce M. said:**
> So far there are nine of us here with the same problem. So I created a thread in General Help: [Errors with message bus daemon]("http://ubuntuforums.org/showthread.php?p=5444742#post5444742") to see if I can pull in some help from that area.

The plea for help was on behalf of all of us, by name. Please don't shoot me for mentioning your name in that post.

"I fell into a burnin' ring of fire ... " :guitar:

Gotta love Johnny Cash. :lolflag:
"X"ing fingers.
Bruce

I think that you will find that there are a lot more than nine users with this problem.  You will find a thread at
 [http://ubuntuforums.org/showthread.php?t=772733](http://ubuntuforums.org/showthread.php?t=772733)
dealing with the problem and proposing a number of different solutions and work-arounds. Unfortunately, none of them has worked for me!  However, you may have a better outcome.

---

### Post by anandbabu20 on 2008-07-24
I had this probelm with Hardy. So I quit Hardy and tried SuSE 11 and Fedora 9. 

Unfortunately SuSE and Fedora gave me more problems and I sadly returned to Hardy.

I cant agree to the statement that this doesn't hurt anything. It prevents my laptop from shutting down! 

If we change the sequence of scripts during shut down process can we prevent this? Like, shut down NM before DBUS?

I am guessing, I do not know how to do that..

Kindly help!

Thanks

---

### Post by Bruce M. on 2008-07-24
> **Amarsingh0793 said:**
> Hi Guys! I'm just wondering, are you having a "Failed to Initialze HAL" Error message at login? If so, I haveposted a solution here: [http://ubuntuforums.org/showthread.php?t=23291](http://ubuntuforums.org/showthread.php?t=23291)

HAL is related to dbus somehow, I think...

Hope this helps you guys :)

Not for me, no problems starting at all.
But thank you for pointing this out.

Have a nice day.
Bruce

---

