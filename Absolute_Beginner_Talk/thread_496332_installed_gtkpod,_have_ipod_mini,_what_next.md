---
title: "installed gtkpod, have ipod mini, what next?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by pcrussell50 on 2007-07-09
the setup:

1]i have an ipod mini that i normally sync with a pc

2]i now have a dual boot system, with dapper on it's own hdd

3]i have installed gtkpod, with libgpod through the package manager

4]my ipod mini mounts perfectly, and is totally readable

the problem:

1]gtkpod will read the mini and display it's entire contents beautifully, [so will rhythmbox, btw], but it will not play any of the songs, even when i right-click and select "play now".

2]unlike in windows, can i populate gtkpod's library with the music from my ipod?

best,
peter

---

### Post by koshari on 2007-07-09
have you got mp3 codecs installed?

---

### Post by pcrussell50 on 2007-07-09
> **koshari said:**
> have you got mp3 codecs installed?

hmmm...good question.   i guess i just assumed that they were already included in gtkpod and/or rhythmbox.  i have a fully current copy of dapper.  would they not come with that?  i'm fairly comfy with synaptic, and have universe selected.  if you tell me which new packages to select to get mp3 codecs i'll go do it.

best,
peter

---

### Post by wolfen69 on 2007-07-09
open synaptic and search for- a2mp3

---

### Post by koshari on 2007-07-09
i think with dapper the package for rythmbox mp3 playback is gstreamer ugly .8 or gstreamer .8 mad packages..

---

### Post by pcrussell50 on 2007-07-09
> **wolfen69 said:**
> open synaptic and search for- a2mp3

installed, and did not work.

regards,
peter

---

### Post by Old Pink on 2007-07-09
> **pcrussell50 said:**
> 1]gtkpod will read the mini and display it's entire contents beautifully, [so will rhythmbox, btw], but it will not play any of the songs, even when i right-click and select "play now".

2]unlike in windows, can i populate gtkpod's library with the music from my ipod?

1) You won't be able to play DRM music you purchased from iTunes. They're .m4p file format and locked up beyond Linux use. There are ways to decode them, but they're time consuming and this forum doesn't condone illegal activity, and nor do I. You can now pay iTunes an extra 40 cents or something to have some of the tracks unlocked, look into "iTunes Plus" on Windows. 

2) I think there was something about this with the libgpod version in Dapper. I had to compile from source, and then compile amaroK over this. This is fixed in Feisty. I may be wrong, but remember something along those lines happening. :)

---

### Post by pcrussell50 on 2007-07-09
> **koshari said:**
> i think with dapper the package for rythmbox mp3 playback is gstreamer ugly .8 or gstreamer .8 mad packages..

installed gstreamer .8 mad...no dice.  couldn't find gstreamer ugly .8, but found gstreamer ugly 10. installed it. no dice either.

hmmm.  just to be sure we are talking about something possible:  my ipod mounts, and it's library shows up in gtkpod and rhythm box...it's just that nothing plays.  in gtkpod, i get a little message that says something like "cannot find xmms" or such.

best,
peter

---

### Post by pcrussell50 on 2007-07-09
> **Old Pink said:**
> 1) You won't be able to play DRM music you purchased from iTunes. They're .m4p file format and locked up beyond Linux use. There are ways to decode them, but they're time consuming and this forum doesn't condone illegal activity, and nor do I. You can now pay iTunes an extra 40 cents or something to have some of the tracks unlocked, look into "iTunes Plus" on Windows. 

2) I think there was something about this with the libgpod version in Dapper. I had to compile from source, and then compile amaroK over this. This is fixed in Feisty. I may be wrong, but remember something along those lines happening. :)

darn, i know i forgot to mention this.  none of my music is purchased from itunes.  it is all unprotected mp3 that was loaded from legal cd's...[or downloaded from napster waaay back when].

best
peter

---

### Post by Anagonda on 2007-07-09
This is my opinion, but you should try program called Floola. It is really easy to use and you can find a version of it to windows too. So same program on both sides.

I had many strange problems with gtkpod, and a few with floola. But there is a thread(use search) where you can give your problems to the program writer. Allways the next update has fixed the problem.

---

### Post by devapea on 2007-07-09
Ive got the exact same problem. I can connect, mount the ipod but when I try to play a song and I get an error message stating something like problem with play command xmms.  I'll try the other play you mentioned too...thanks

---

### Post by koshari on 2007-07-10
personally i use amarok because it beats the pants of rythmbox (and any other music players in windows mac or linux). but here is a snipper from another thread, to get mp3 going in rhythmbox


Re: Rhythmbox MP does not play "MP3" files
Quote:
jem7v: I'd guess it's in one of these four:
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverseRead this page for a little more information: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
NOW IT WORKS
Thanks jem7v.
I used
Code:

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
 gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly
 gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 
 libxine-extracodecs ogle ogle-gui

because I could not figure out which file only would do the trick!

---

### Post by pcrussell50 on 2007-07-27
woohoo! a self-guided solution!  i decided to make and play with a feisty live cd.  plugged in my ipod mini?  mounts right up, sweet, [but it did this in dapper, too].  then rhythm box opens and does it's self-guided setup, i defer pointing it to any library because i'm not setting up a library just for a live cd session.  next, i see that rhythmbox can read the contents of my ipod, and not just in the codified gibberish format that they give it to you in if you list it's contents in DOS.  then i try to play a song, and i get the red circle with a white dash in the middle...failure...as expected.  no biggie.  so i close rhythmbox, and just for kicks open the ipod icon directly, and explore the list of songs in their raw, gibberish form.  for grins again, i double-click on one of them, not knowing what it was called.  lo and behold, synaptic opens with a list of suggested packets to download/install, and asks if i would like to.  i say YES.  then it warns me that what i'm doing might be illegal, [playing music i already own?], and i tell it to continue.  it does.  when it finishes, my song starts playing.  hmmm...cool, but i can't make out the song titles in the "explorer" window, they're in code.  for grins, i decide to open rhythmbox again. and again, it reads my ipod and displays it's contents like a champ, as always.  BUUUT, this time it will play anything i choose, right off my ipod!  no red circle with the white dash in the middle.   VICTORY!

this was all i wanted when i started this thread, since i'm still dual booting with windoze for now, and am managing my 'pod with itunes.  one day, when i go full commitment to ubuntu, i'll look at totally managing my ipod from ubuntu.  for practice, i'll experiment with the ipod i got for $10 at an estate sale, [a 4-gig mini that works].

i've been playing with floola, and gtkpod.  not tried amarok.  tempted to try yamipod, too.  is there a way to ask about which one is the least buggy without starting an opinionfest with equal measures in each camp? remember, this is an ipod mini.  pics and videos are a non-consideration.  i do want to be able to sync a podcast, though.

-peter

---

### Post by Espreon on 2007-07-27
> **Old Pink said:**
> 1) You won't be able to play DRM music you purchased from iTunes. They're .m4p file format and locked up beyond Linux use. There are ways to decode them, but they're time consuming and this forum doesn't condone illegal activity, and nor do I. You can now pay iTunes an extra 40 cents or something to have some of the tracks unlocked, look into "iTunes Plus" on Windows. 

2) I think there was something about this with the libgpod version in Dapper. I had to compile from source, and then compile amaroK over this. This is fixed in Feisty. I may be wrong, but remember something along those lines happening. :)

It is easy to legally remove the DRM 4 free, just burn the .mp4 s (the song files bought from iTunes) to a CD, and rip them with Sound Juicer to a format like .ogg simple and legal as that!

---

### Post by pcrussell50 on 2007-07-27
> **Espreon said:**
> It is easy to legally remove the DRM 4 free, just burn the .mp4 s (the song files bought from iTunes) to a CD, and rip them with Sound Juicer to a format like .ogg simple and legal as that!

Yep, the old "analog hole", they call it.  I haven't had to use it, because all my music is already DRM-free.  everything on my ipod is bare mp3.  i've not bought a single song off itunes music store...ever.

-peter

---

### Post by Espreon on 2007-07-27
Guess what? Me neither! Even so isn't grand that the concept of analog hole exists?

---

