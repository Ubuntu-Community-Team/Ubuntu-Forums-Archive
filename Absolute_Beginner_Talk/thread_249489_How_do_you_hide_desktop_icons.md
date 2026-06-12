---
title: "How do you hide desktop icons ?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2006-09-02
Thread title pretty much says it all. I want to hide my desktop items, and just have a nice clean wallpaper and some desklettes showing. Thanks. 

Doug

---

### Post by benfindlay on 2006-09-02
Just delete the ones you don't want

---

### Post by Sweet Spot on 2006-09-02
That's actually not an option. I'm talking about the ones which are put there by Ubuntu. Such as hda1  New Volume etc.. They're drives. The only option available, is to unmount them, which obviously, I don't want to do. Is there no option to hide desktop items or anything like that ?

---

### Post by mostwanted on 2006-09-02
> **Sweet Spot said:**
> That's actually not an option. I'm talking about the ones which are put there by Ubuntu. Such as hda1  New Volume etc.. They're drives. The only option available, is to unmount them, which obviously, I don't want to do. Is there no option to hide desktop items or anything like that ?

Start gconf-editor and go to /apps/nautilus/desktop

Untick those options you don't want (volumes_visible is probably the only one on).

---

### Post by ron999 on 2006-09-02
Hi Sweet Spot
If it's your mounted drive icons that you want to shift, this is how:-

Open a terminal and enter

gconf-editor

Then when Configuration Editor opens up click apps then nautilus then desktop then volumes_visible.

Set it to false by unticking it. Then close it.

edit, mostwanted beat me to it!

---

### Post by jamesford on 2006-09-02
if u only wanna show some icons, like mounted usb/cd/dvd drives, while not showing mounted hdd partitions, those u dont wanna see can be hidden nicely behind a gdesklet ;)

---

### Post by Sweet Spot on 2006-09-02
Brilliant ! Thank you everybody, that was of great help. I would imagine that gconf is a pretty powerful tool hu ? Something I should get familiar with I suppose. Though I honestly think, that something like what I was just asking for (and yes, achieved) should be a more simple process, considering what the devs of Ubuntu want it to be associated as. Ie; noob ready distro etc.. 

Things like that really ought to be automated with a little script. Perhaps in the next revision/build ? IMO, it would be a definite improvement towards moving Ubuntu into the desktop ready stage... 

Doug

---

### Post by xpod on 2006-09-02
come on.....THAT was`nt hard was it.I think the dev`s need to look at more important things like how the hell i turn it off SO i can go to bed.

I know the buttons there but i think it needs some automatic shutdown for new users cause i cant hit that button for the life of me...

Now THATS hard.......getting rid of the icon was i piece of cake](*,) :biggrin:

---

### Post by Sweet Spot on 2006-09-02
I agree, it wasn't hard, technically speaking. On the other hand, such a simple task, shouldn't need to be hidden in such a way. For every person who might be wondering the same thing, they'll probably create a thread on just the same thing I did (unless they're good and search) which should be unnecessary IMO. 

My point here is that there are probably a LOT of tiny LITTLE things just like that, which could use the same sort of attention, so that Ubuntu is that much more user (*noob) friendly. Lots of little things, when not tended to, usually turn into a bigger problem overall. 

As for your problem, might I suggest you get your mate to just "pull the plug", so to speak ?  If no mate is present, my other suggestion would be to just shut your eyes, and imagine that your actually using Windows ? That'll do it for ya. :twisted:

Doug

---

### Post by xpod on 2006-09-02
I dont know....I quite like the fiddling about to see how things work.
I only used windows for a few months so cant give any expert opinions but
i much prefer messing around to "see" how things work as apose to the messing about i had to do in windows to "get" things working again.

Ive had my calamitys here but only cause i caused them:-\" .

IT.S ALL GOOD

---

### Post by toasted on 2006-09-03
While you are in the config editor, if you go to apps/nautilus/desktop and check computer_icon_visible you will have something like "My Computer" in Windows

---

