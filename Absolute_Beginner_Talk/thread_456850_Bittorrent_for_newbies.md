---
title: "Bittorrent for newbies"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Cod on 2007-05-28
Hi folks,
I'm a newbie to Ubuntu and have liked what I've seen so far.  I have my wifi set up and everything seems to be ticking along nicely.  I now have a problem with using bittorrent.  When I used WIndows I used Utorrent and could get some high download speeds (up in the 100 kb/s) depending on seeders, without having to adjust any settings.

I've recently installed Ktorrent and I'm struggling to get it to download anything.  Sometimes a file will trickle in at 1 kb/s but most of the time it just says stalled.  This is the case for files with 1000s of seeders.

I've looked through the forums for help and there is lots of talk about opening ports and so on.  I've tried to follow this but have struggled.  I've installed Firestarter and tried to open ports using the Policy thing but to be honest I don't know what I'm doing and nothing I've tried has enabled me to download anything.  I have the UPnP plugin and have tried forwarding ports etc.

Can anyone help a newbie with this?  Please be gentle - I'm not a technophobe but I don't really understand networking terminology (e.g. ports, ips etc).

I'm using Feisty on a laptop that is connected to the internet using wifi via my wireless router at home.  I believe that the router has a firewall.

Thanks in advance

---

### Post by ugm6hr on 2007-05-28
*When you used Windows* were you using the same Wireless router to torrent?

If the router has a firewall - you will need to "forward ports" on that too.

As for Ubuntu:
1. Open Ktorrent
2. Go to Settings -> Configure Ktorrent
3. In "Downloads" make a note of the numbers in the boxes beside "Port" and "UDP tracker port"
4. Close Ktorrent
5. Open Firestarter (it needs password)
6. In "Policy" tab (make sure Editing says "inbound traffic policy"), right-click lower white box (Allow Service) and select "Add Rule"
7. In Name - select Bittorrent (or type Ktorrent), in Port - type the Port number you noted above, and click "Anyone".
8. This should just work now - but I believe it's better to repeat steps 6-8 with the "UDP Tracker Port" number you noted too.
9. Click "Apply Policy"

Try that.  Remember you will have to run Firestarter each time you reboot if you want to enable torrents.

If it doesn't work - you'll have to enable port forwarding on your router too - using the same port numbers you noted above.  How you do that depends on your router - try this:
[http://portforward.com/routers.htm](http://portforward.com/routers.htm)

---

### Post by ggaaron on 2007-05-28
Ktorrent works good for me, but i have heard that for some people it has very low download, same as other has very low for me=/ Try using different clients, but Ktorrent works good for me, and I have my laptop connected to a router and then to a next router (not owned by me), so I can't do any port forwarding.

---

### Post by Cod on 2007-05-28
Hi,
Thanks for the prompt advice.  I followed your instructions but still have the same problem.  Anything i try to download just says 'Stalled'.  It is the same the router that I used successfully with Windows.  I'll take a look at the link you sent for adjusting the settings on the router but is it really necessary as the router works fine under Windows?

Any other ideas?

Stupid question:  having set up the policy in Firestarter, Firestarter it should be Active right?  Not that it makes a difference to downloading.

---

### Post by ggaaron on 2007-05-28
I have a firestarter with permissive outbound policy and it all works.

---

### Post by ggaaron on 2007-05-28
Maybe you could give the torrent that you are trying to download, so I could test if it works for me, if it will then it is probably problem with your configuration.

---

### Post by Cod on 2007-05-28
Hi ggaaron

Thanks for offering to help out.  To test my set up I've been trying to download Open Office (I know I already have it and I know you can get it from the respositories but I thought I'd test my set up with a legitimate torrent).

From the Open Office website I went through the download options and then something pinged up in Ktorrent.  From what I can tell, there are several trackers:

[http://borft.student.utwente.nl:6969/announce](http://borft.student.utwente.nl:6969/announce)
[http://core-tracker.depthstrike.com:9800/announce](http://core-tracker.depthstrike.com:9800/announce)
[http://core-tracker.enlist-a-distro.net:9800/announce](http://core-tracker.enlist-a-distro.net:9800/announce)
[http://www.ooodev.org:6969/announce](http://www.ooodev.org:6969/announce)

and the file is called:

OOo_2.2.0_LinuxIntel_install_en-US.tar.gz

Apparently there are 31 seeders (not many) but I just have a stalled download.

If you need more information, let me know

---

### Post by ggaaron on 2007-05-28
Sorry, I think I won't be able to test it for some time - I'm upgrading kde, and ktorrent doesn't start, but I think it won't be long until it finishes, and after restart I'll test it.

OO, English with JRE? - this is the right torrent?

---

### Post by Cod on 2007-05-28
Didn't go for the JRE option, just went for Open Office 2.2
I can certainly try that one as well though.

Thanks for your help

---

### Post by ugm6hr on 2007-05-28
> **Cod said:**
> Hi,
Thanks for the prompt advice.  I followed your instructions but still have the same problem.  Anything i try to download just says 'Stalled'.  It is the same the router that I used successfully with Windows.  I'll take a look at the link you sent for adjusting the settings on the router but is it really necessary as the router works fine under Windows?

Any other ideas?

Stupid question:  having set up the policy in Firestarter, Firestarter it should be Active right?  Not that it makes a difference to downloading.

I won't interfere after this - I promise.... but I do have one other idea.

Do you still have Windows?  If so - go to whatever torrent engine you use in Windows, and find the Port that it uses (it will be in Preferences / Configuration).  Then try entering it into the Configure Ktorrent "Port" box.  You may have to re-edit Firestarter as previously (or just watch the "Events" tab - it will let you know if it's blocking anything).  

The reason I suggest this is that some ports transfer slowly because ISPs block them (as explained [http://forums.torrentspy.com/showthread.php?t=24378](http://forums.torrentspy.com/showthread.php?t=24378))

---

### Post by ggaaron on 2007-05-28
My download almost immediately jumped up to about 100kb/s

Maybe your client isn't the latest one?
I haven't changed almost anything in the configuration...

---

### Post by renfrowasd on 2008-01-07
Hi, I am having the same problem with ktorrent, that any file i select to download says "stalled"  

I don't have a router, I'm on a school network, and I installed gutsy over my winter break.  I could download freely with windows on the network before, but now I cannot.  I allowed ktorrent to use the ports it suggested in firestarter, but I still get the "stalled" status.  When I look in firestarter, ktorrent isn't even on the "active connections"  list.  How do I fix this?!  I'm new to ubuntu and I'm not using wireless.  Thanks!

---

### Post by hyper_ch on 2008-01-07
> **ugm6hr said:**
> Remember you will have to run Firestarter each time you reboot if you want to enable torrents.

That's wrong. You don't have to run Firestarter each time after reboot.


If you want to test rTorrent, let me know. It's a terminal based client, doesn't hog your system like azureus and ktorrent (and also the founders of TPB run rTorrent)...

Btw, you don't use Comcast, do you?

---

