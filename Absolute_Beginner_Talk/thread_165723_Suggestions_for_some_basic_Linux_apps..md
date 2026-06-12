---
title: "Suggestions for some basic Linux apps."
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Just4 on 2006-04-25
I'm looking for a good multimedia player and a p2p program, I want something light I can run in the background for mp3's exclusively (On my Windows box I run  a small prog called 1by1 for my mp3's) and possibly something for some light video watching (Though not much, not too much into videos, mostly I watch them on my Windows machine.) - as for p2p, is there anything thats equal to Shareaza and BitComet on Linux? I've also been looking for an IRC client, I've become quite used to mIRC and have quite a bit of scripts that I've made that I use daily, is there any IRC client on Linux that can use mIRC scripts? Can I setup Wine to run mIRC (Plus a few other windows-only apps.)? Is it necessary to use a firewall? (Is there even a software firewall available for Linux?) I'm on DSL and I am connecting through a NAT router, so I know thats a pretty good hardware firewall in itself, but I also know its good to have some extra system hardening. I'm also looking for some CD-burning software. Thanks for any suggestions/help.

---

### Post by colo on 2006-04-25
I'm looking for a good multimedia player
mplayer

and a p2p program,
mldonkey

I want something light I can run in the background for mp3's exclusively (On my Windows box I run  a small prog called 1by1 for my mp3's)
mplayer,mp3blaster, beep-media-player, mpg321

and possibly something for some light video watching (Though not much, not too much into videos, mostly I watch them on my Windows machine.)
mplayer

as for p2p, is there anything thats equal to Shareaza and BitComet on Linux?
mldonkey

I've also been looking for an IRC client, I've become quite used to mIRC and have quite a bit of scripts that I've made that I use daily, is there any IRC client on Linux that can use mIRC scripts?
no

Can I setup Wine to run mIRC (Plus a few other windows-only apps.)?
yes

Is it necessary to use a firewall?
no

(Is there even a software firewall available for Linux?)
none of the "Personal Firewall"-placebo style "firewalls" exist for GNU/Linux. There's a packet filter included in the kernel (netfilter), and its front-end is called iptables. You don't need to set it up most probably, GNU/Linux is fine without such kind of things in most cases.

I'm also looking for some CD-burning software.
k3b, graveman (both are front-ends for cdrdao and cdrecord)


Hth.

---

### Post by AndyM on 2006-04-25
If you're looking for mp3s, I'd recommend Nicotine, which is a Soulseek client.  CD-burning software and video playing software should have come with your installation, but you may need to install some proprietary codecs as well.

---

### Post by nalmeth on 2006-04-25
[QUOTE=Just4]I'm looking for a good multimedia player and a p2p program, I want something light I can run in the background for mp3's exclusively (On my Windows box I run  a small prog called 1by1 for my mp3's) and possibly something for some light video watching (Though not much, not too much into videos, mostly I watch them on my Windows machine.) - as for p2p, is there anything thats equal to Shareaza and BitComet on Linux? I've also been looking for an IRC client, I've become quite used to mIRC and have quite a bit of scripts that I've made that I use daily, is there any IRC client on Linux that can use mIRC scripts? Can I setup Wine to run mIRC (Plus a few other windows-only apps.)? Is it necessary to use a firewall? (Is there even a software firewall available for Linux?) I'm on DSL and I am connecting through a NAT router, so I know thats a pretty good hardware firewall in itself, but I also know its good to have some extra system hardening. I'm also looking for some CD-burning software. Thanks for any suggestions/help.[/QUOTE]
If you're looking for something really light for mp3's (like with no track/album info) beep mulitmedia player or xmms are good for that, though it can get so light as to just play in the terminal. YOu can have as heavy or light as you want.
Same thing for video. Totem (the default in ubuntu) is pretty light, and when I'm doing a lot, I'll stick videos and songs in the playlist in totem, and let it run in the background. 
The lightest way I've found to play videos again is in the terminal.
mplayer whatever.avi
I think you can get bitcomet on linux, but ubuntu comes with bittorrent. Other torrent apps around are azureus (really really heavy, but tons and tons of info), bittornado, ktorrent, and I think you can run utorrent in wine.
For p2p, there is a whole range of things you can do. 
mldonkey can run fasttrack (kazaa) gnutella (limewire) ares and openft (shareaza I think?), as well as torrents, but is difficult to set up.
You can get limewire and frostwire, but I prefer apollon for speed and usability.
in a terminal
sudo apt-get install gift apollon libfasttrack-gift
when you launch apollon, tell it to find your plugins in /usr/share/gift
I think xchat is equivalent to mIRC, but I would wait for verification on that.
God I haven't used mIRC in ages!
Don't know if mIRC can be run in wine, check app database at winehq
You have a firewall setup within ubuntu already called iptables. You can configure it with the frontend 'firestarter'
sudo apt-get install firestarter
I don't place this step as any priority, but suit yourself
For CD-burning, my all time favorite app is 'K3B'
sudo apt-get install k3b
gnomebaker is quite good too, but don't like as much as k3b
you can get nero for linux but it's not worth it.
k3b all the way
EDIT:
Oh, and get automatix or easy ubuntu to setup non-free codecs, and lots of other stuff you might want

---

### Post by stfu on 2006-04-25
Xmms is a winamp 2 clone that can be found on repositories. VLC player is pretty good choice for videos with its builtin codecs. For bittorrent there's always Azureus. Dunno about other Shareaza networks, I guess there's equivalent. 

Xchat is bundled with ubuntu, but some people like irssi more. It's textbased though. I guess you could try mIRC through wine, should work pretty much out of the box. K3b is a really good cd-burner, though as it's KDE program, it needs some additional libraries installed in Gnome. Linux has iptables as a firewall. Firestarter is widely used frontend for easier tweaking of it.

There's a big thread about windows - linux apps somewhere.

---

### Post by stfu on 2006-04-25
Check this thread for programs.
[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

---

### Post by Indras on 2006-07-02
Shareaza runs just fine in Ubuntu with Wine.  Dig around the Shareaza website for installation instructions.  Here's a screenshot of it running on my system (taken just a few seconds ago):

[http://img407.imageshack.us/my.php?image=screenshot5gq.png](http://img407.imageshack.us/my.php?image=screenshot5gq.png)

---

