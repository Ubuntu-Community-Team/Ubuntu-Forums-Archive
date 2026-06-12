---
title: "Will &quot;Syncronize iPod&quot; in Banshee delete my music?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-03-28
As the title says.

I have a collection of 3250 songs I can't afford to lose.

I have a ripped cd in my Library.

How do I sync it to my iPod in Banshee?

By the way, is there a way with Banshee to rip to mp3? I selected for it to rip as 190kb/s AAC, but it looks like it ripped as ogg.

---

### Post by alex-desktop79 on 2007-03-29
bump.

It's a yes/no question.
Surely someone knows.

---

### Post by alex-desktop79 on 2007-03-29
re-bump.
anything?

---

### Post by crankcaller on 2007-03-29
> **alex-desktop79 said:**
> re-bump.
anything?


why not try here:
[http://banshee-project.org/Main_Page](http://banshee-project.org/Main_Page)

Either the forums or the wiki/faq might help...

---

### Post by alex-desktop79 on 2007-03-29
Already looked. I can't believe no one knows this. :P

---

### Post by aysiu on 2007-03-29
No one knows this.

---

### Post by alex-desktop79 on 2007-03-30
No one has ever dared press the button?

---

### Post by aysiu on 2007-03-30
I can't speak for others, but I don't have an iPod. I have a Sandisk player. And I use Rhythmbox, not Banshee. So, at least for me, it's not a matter of "daring" to press the button or not. The situation is irrelevant. I'm sure many others have not been in the situation to "dare" to press it. Maybe they use AmaroK or Rhythmbox for their iPods or don't have iPods... or just don't feel the need to synchronize in Banshee.

Or... maybe they just don't dare to do it.

---

### Post by familyjules74123 on 2007-03-30
do you have enough room to backup your music?  possibly a friend who can lend you his external hard drive or something of the sort? if so, backup your music and try it out.  I believe that the sync option, in the real itunes anyway will not erase your files, or at least it hasn't done it to me.  Again, backup your music if you want to try and absolutely can't afford to lose the music, and then give it a whirl.  Post your results so if the question comes up again we will not have to bump a thread several times.

---

### Post by aysiu on 2007-03-30
Did a little Google searching, and according to [this page](http://www.gnomejournal.org/article/30/the-banshee-music-player-an-introduction), you probably want to do *Automatic merge* instead of *Automatic sync*: > There are three ways to manage the music on your iPod.

**Manually** &#8211; You can browse your iPod, drag music between your library and the iPod.

**Automatically sync** &#8211; Automatically copies everything in your library to the iPod.

**Automatic merge** &#8211; All the music on your iPod that is not in your library is downloaded to your library, and all the music that is in your library and not in your iPod is uploaded to your iPod.

When the iPod is selected, you will be able to see some information about your iPod at the bottom left. Including disk usage, and some buttons (sync, properties, and eject).

---

### Post by alex-desktop79 on 2007-03-30
That menu doesn't exist in 0.12.0, and I cant find it.

---

### Post by aysiu on 2007-03-30
Isn't 0.12 the latest version? Kind of odd they'd take *out* a feature...

---

### Post by sushii. on 2007-03-30
Hmm.. well sync in itunes means update your ipod to your current library, so if you have no songs in your library, and you sinc it, then your library will go on to your ipod (which is nothing). If that made sense. So yeah, it would probably erase everything. You can just drag and drop songs onto your ipod to get them on..

---

### Post by aysiu on 2007-03-30
Remind me what the issue here is--you don't have enough space on your hard drive to just back up all the songs? Is that correct?

---

### Post by alex-desktop79 on 2007-03-30
That's correct.
I also have USB 1.0 so that's a no go.
Click and drag shows them on my iPod, I can even play them. But they appear there with no delay and once the iPod is unplugged, they are gone.
I find gtkpod quite an inconvenient way to sync to the ipod.
(I wish I had another player...)

To sushii:
That's what I'm scared of, bad experience. :)

---

### Post by gorded on 2007-04-01
If you press synchromicze ipod banshee will create a copy of you banshee
music database on your ipod. Its basically updating your ipod.

It's bad wording if you ask me :)

---

### Post by macogw on 2007-04-01
Well, you might want to go through with Audio Tag Tool and tag all the files first so they'll show right on the iPod.  Banshee doesn't really tag them it just pretends to)

---

### Post by Dragonbite on 2007-05-31
I have an iPod and Banshee and synched up last night. **Automatically sync** tries to upload EVERYTHING in Banshee (which is more than my little 1GB iPod can handle, so it erred-out)

I did **Manually **and it synched my physical iPod with the tunes I had on the iPod in Banshee (I actually deleted all of the songs that were in the iPod and replaced them with another collection of songs in Banshee).

It cleared the iPod of the existing songs and copied all of the songs I had selected (dragged into the iPod icon in Banshee) without any problems.

I did, however, have the problem with the iTunes database, which it did not build correctly and so I could not play the iPod even though the songs were present.

I ended up going into Gktpod, extracted the songs from the ipod (the first button on top), which informed me there was an error with the database and it was going to try its best to fix everything.  It did extract all of my songs.  When  I then resynched in gtkpod it fixed the database (didn't have to touch the songs because they were already there).

I'm actually listening to the iPod right now as I type this! :)

---

### Post by sdswingr on 2007-06-14
well it won't delete it, it will just make it completely inaccessable. Even on the ipod itself...I hate Banshee right now, accidently pushed wrong button...

---

### Post by Dragonbite on 2007-06-15
> **sdswingr said:**
> well it won't delete it, it will just make it completely inaccessable. Even on the ipod itself...I hate Banshee right now, accidently pushed wrong button...Gtkpod seems to have the best iPod and iPod database reliability, you may want to install that and run the iPod through it to see if it clears things up and then try Banshee again.

Note: I claim no responsibility for what happens. :)

---

