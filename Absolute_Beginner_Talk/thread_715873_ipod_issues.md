---
title: "ipod issues"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by balakumar on 2008-03-05
I am writing this after extensively going through the forums on ipod and itunes.

I am very very interested in my ipod. I am also equally convinced about ubuntu.

I find that my 80GB ipod classic does not work with ubuntu despite Amarok, Banshee and gtkpod.

I have the following problem:

1. The hard drive of the ipod works. But the ipod doesnot show any music files.

How to get around these issues?

Thanks in advance

---

### Post by Kiri on 2008-03-05
What software are you using to try and see / play the music from your ipod?

Side note: if you are into linux, you might be interested in checking out rockbox or ipodlinux...

---

### Post by mangurt on 2008-03-05
> **Kiri said:**
> What software are you using to try and see / play the music from your ipod?

Side note: if you are into linux, you might be interested in checking out rockbox or ipodlinux...

+1 for Rockbox :)

Did you set up the correct ipod in amorak?  I know I could not do anything with my ipod with gtkpod, but once I set up Amorok, I was transferring music with no problem.

---

### Post by saj0577 on 2008-03-05
> **mangurt said:**
> +1 for Rockbox :)

Did you set up the correct ipod in amorak?  I know I could not do anything with my ipod with gtkpod, but once I set up Amorok, I was transferring music with no problem.

I know it is a slight side note so i apologize but when you put music on your ipod from amarok is it still in the same file structure as using itunes(the files on your ipod not easily seen through a "Computer" style directory viewer. Or is it just the basic folders of the artist names with no "encryption"(used losely)

Saj

---

### Post by balakumar on 2008-03-06
The fact is i have read a lot about the ipod 6G not working in the gusty os. And i think i am starting to believe it. The main reason i got into linux was that xp was bad. to the core. I have two problems with gusty.

The audio does not work
and my new ipod does not work,.
\

in amarok the wizard that opened up let me choose the type of ipod i owned.
i chose 6G classic. BUt when i open the ipod from other software it shows up as a 5G ipod.

And the 16 char number that i used in floolaturn out to show up as the wrong one.

Moreover the ipod does not work with itunes now. It ejects from the pc as soon as it is connected.

In amarok, my ipod gets added after configuration, but even there it disconnects now.
I have no clue whats going on.

please help me out.

thanks in advance.

---

### Post by catroaring on 2008-03-06
i use songbird works like a pro.  [http://www.songbirdnest.com/](http://www.songbirdnest.com/)

---

### Post by superzorro on 2008-03-06
I would reset the ipod and then uninstall gtkpod and after that follow this thread:

[http://ubuntuforums.org/showthread.php?t=619615](http://ubuntuforums.org/showthread.php?t=619615)


You'lle need to compile the libgpod in order to use the ipod.

After that it should work

---

### Post by balakumar on 2008-03-07
I tried to install song bird and managed to install it correctly with some guidance.

It asks us to download the ipod device driver to sync with the ipod. I tried to do that, the software downloaded a couple of files about 1 mb inorder to get the device driver. The device driver seems to be installed as the addons list indicates that there has been a change in the assons and it allows be to uninstall the device driver addon. But the addon does not appear as a tab on the preferences page. It looks different when compared to the insallation procedure guidance pictures and snapshots.

Guys help me out. I really want to stay with ubuntu and it rocks. The sound card does not seem to work even now. Its amazing to know that intel board sound cards are not recognised by the best OS ever.

thanks in advance

---

### Post by tgalati4 on 2008-03-07
Post the output of:

>lspci -v

---

