---
title: "Command line based system?"
date: 2008-02-03
forum: Arch and derivatives
---

### Post by TheOrangePeanut on 2008-02-03
I have a PC at my parents house that is a few years old and I currently run Xubuntu on it, but it is still relatively slow.  I only use it for surfing the internet, messaging, and listening to music. 

I was thinking it might be cool to convert it to a terminal based computer because it'd be a lot faster.  All the websites I visit are mostly text based (forums, programming websites, wikipedia, etc) so flash and graphics isn't really necessary.  

I want to use Arch to do this.  I've had Arch installed on that PC once before but I didn't have time to set it up properly so I reinstalled Xubuntu on it so I could SSH into it from my house and use it as a file server.  Basically, what I'm getting at, is what programs do I need?

Browser:  Links, Lynx, eLinks (whats the difference,  Which is better?)
Terminal AIM client:  No idea
Terminal Music player:  mtp?  Is that even it?  I can't remember.
Text editor: vim

Any other suggestions about what kind of things I should install?  Remember, no X or any graphics... ncursors would be okay I guess.

---

### Post by Tenken on 2008-02-03
For the IM client you could use [finch]("http://aur.archlinux.org/packages.php?do_Details=1&ID=14679&O=0&L=0&C=0&K=finch&SB=n&SO=a&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd")  which is a text based version of pidgin, it's in the AUR. The music player you are looking for is [mpd]("http://musicpd.org") and there are a couple of different [text-based]("http://musicpd.org/clients.shtml") front ends for it.

---

### Post by Rumor on 2008-02-03
You would probably be interested in this old thread, especially in what can be done using framebuffer.
[http://ubuntuforums.org/showthread.php?t=260946](http://ubuntuforums.org/showthread.php?t=260946)

You can play music, watch video and do other things from an installation without X that you might think you'd have to rule out.

There have been a few threads about the apps one would use  on a CLI only system. Here are a couple:

[http://ubuntuforums.org/showthread.php?t=680000](http://ubuntuforums.org/showthread.php?t=680000)
[http://ubuntuforums.org/showthread.php?t=669648](http://ubuntuforums.org/showthread.php?t=669648)

---

### Post by TheOrangePeanut on 2008-02-03
Wow, thanks for the links.  I can't wait to go to my parents house so I can try this out :)

---

### Post by kerry_s on 2008-02-03
wow, thats a bit drastic.
what are your specs?
have you considered using something lighter than xubuntu, it's not really as light as it claims to be. there's lighter *ubuntu distros such as fluxbuntu, you might even want to look at mini distros such as puppy or dsl.
before you go the arch route you might consider doing a buntu minimal and build it to your needs.

minimal how to-> [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
i recommend DSL for any thing old and needs saving-> [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

distrowatch is a good place to find distros, read reviews, etc...-> [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by drcranium on 2008-02-04
You don't have to get rid of X.  That will make your job pretty hard.  Try using X, and then Awesome as your Wm.  Mine only uses about 70MB of ram with xcompmgr, mpd, ncmpc(mpd client), and a terminal or two.  I recommend Awesome because its a mostly tiling WM.  This allows you to use CLI apps very effectively.  Program recs:
AIM:Finch
Email: Mutt
Web:Lynx or any of those(I usually just use swiftfox)
Music:MPD and a client(Sonata for GUI or NCMPC for cli)
IRC: Irssi
Editor:Vim or Nano
If you use X I would recommend booting straight into it.  A guide is in the wiki.  Otherwise, use the SLiM login manager(Also on the wiki).

---

### Post by TheOrangePeanut on 2008-02-04
I've used DSL on this PC and it's plenty fast, but this is also my experimental box which is why I want to use a command line interface system.  You know, just to see if it's feasible to use day to day :).  I don't want to use Ubuntu because, as I just said, this is my experimental box and I really, really do like Arch.  Pacman is a great package manager and I really dig the KISS / do it yourself way of Arch.

---

### Post by kerry_s on 2008-02-04
> **TheOrangePeanut said:**
> I've used DSL on this PC and it's plenty fast, but this is also my experimental box which is why I want to use a command line interface system.  You know, just to see if it's feasible to use day to day :).  I don't want to use Ubuntu because, as I just said, this is my experimental box and I really, really do like Arch.  Pacman is a great package manager and I really dig the KISS / do it yourself way of Arch.

gottcha, then i suggest
web-> links2
filemanager/editor-> mc

---

### Post by andrew.46 on 2008-02-13
Hi,

 Can I suggest my 3 most favourite cli applications, each with a walkthrough on these forums:

[LIST=1]
[*][slrn]("http://ubuntuforums.org/showthread.php?t=475246"): An absolutely amazing console newsreader, currently under *very* active development. 
[*][leafnode 2]("http://ubuntuforums.org/showthread.php?t=676837"): The perfect complement to slrn, an NNTP proxy server.
[*][mplayer]("http://ubuntuforums.org/showthread.php?t=558538"): Just leave out the --enable-gui and --enable-menu options and you have a very powerful cli movie player / music player etc.
[/LIST]

I use these applications every day, and in fact I wrote the walkthroughs :-) The instructions can easily be modified to suit other Linux distros, especially those for slrn and leafnode 2.

                Andrew

---

### Post by ynnhoj on 2008-02-13
gnu screen is a must.  [dvtm](http://www.brain-dump.org/projects/dvtm/) is also pretty nifty.

---

### Post by RedSquirrel on 2008-02-14
abcde is great for ripping & encoding.

---

### Post by bwtranch on 2008-02-16
> **andrew.46 said:**
> Hi,

 Can I suggest my 3 most favourite cli applications, each with a walkthrough on these forums:

[LIST=1]
[*][slrn]("http://ubuntuforums.org/showthread.php?t=475246"): An absolutely amazing console newsreader, currently under *very* active development. 
[*][leafnode 2]("http://ubuntuforums.org/showthread.php?t=676837"): The perfect complement to slrn, an NNTP proxy server.
[*][mplayer]("http://ubuntuforums.org/showthread.php?t=558538"): Just leave out the --enable-gui and --enable-menu options and you have a very powerful cli movie player / music player etc.
[/LIST]

I use these applications every day, and in fact I wrote the walkthroughs :-) The instructions can easily be modified to suit other Linux distros, especially those for slrn and leafnode 2.

                Andrew
Very useful.

---

### Post by chris4585 on 2008-04-06
i've heard that mplayer can play movies in cli with framebuffer, but the most i ever get is just sound... any help please?

---

### Post by fwojciec on 2008-04-06
> **chris4585 said:**
> i've heard that mplayer can play movies in cli with framebuffer, but the most i ever get is just sound... any help please?

You could try something like:
> mplayer -vo fbdev2 -fs -zoom -x 1024 -y 768
Change the size as appropriate, of course.

---

### Post by chris4585 on 2008-04-06
i get the effor [fbdev2] can't open /dev/fb0: no such file or directory
error opening/initializing the selected video_out (-vo) device

---

### Post by fwojciec on 2008-04-06
You are in framebuffer console, right?
This probably doesn't work on all video drivers, though there might be some workarounds...  I'd suggest searching for "mplayer framebuffer" on Arch forums and looking through what you find -- I remember quite a few discussions about this on Arch forums.

---

### Post by chris4585 on 2008-04-06
> **fwojciec said:**
> You are in framebuffer console, right?
This probably doesn't work on all video drivers, though there might be some workarounds...  I'd suggest searching for "mplayer framebuffer" on Arch forums and looking through what you find -- I remember quite a few discussions about this on Arch forums.

i'm on cli mode, i can view photos... if that answers your question, i'll look on the arch forums, i have searched before this with no luck, thanks for the help! :)

---

### Post by K.Mandla on 2008-04-07
[http://gentoo-wiki.com/HOWTO_MPlayer_on_Framebuffer](http://gentoo-wiki.com/HOWTO_MPlayer_on_Framebuffer)

The Gentoo wiki knows all.

---

### Post by chris4585 on 2008-04-07
thanks K.mandla i'll have to check this out when i get home (at school atm)

---

