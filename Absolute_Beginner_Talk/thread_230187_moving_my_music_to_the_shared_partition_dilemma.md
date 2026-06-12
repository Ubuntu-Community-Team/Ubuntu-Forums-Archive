---
title: "moving my music to the shared partition dilemma"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-05
Originally I was going to keep my music on my Windows partition, but I've decided it might be smarter to have them on the shared partition instead, and make the Windows partition that much smaller. 

But here's my problem: according the iTunes help file, you can choose a new place to move all your music, but as of yet I don't have my HD partitioned. But I can't partition it until I delete all my music so I can free up the extra 10GB.

So how do I do this? Do I just change the location to store my music, then delete the music manually, and when I plug in my iPod again it will put all the songs from my iPod into the new location (which will be the shared partition)?

I don't want to mess this up and lose my music, or create a situation where iTunes can't read from the new location, etc.

Thanks.

---

### Post by sitedesign on 2006-08-05
why don't you boot inot linux then copy the music from the windows partition onto your linux partition, then whilst still in linux resize your windows partition and create the new shared partition.
Then copy the music back from the linux partition to the new shared partition.

Hope that helps, god luck. The move to Linux will make life so much easier when you are used to it. Windows will soon seem pointless with all the missing tools and speed.

---

### Post by em3raldxiii on 2006-08-05
Well, since on one else answered ... *EDIT:  Seems I took too long to answer and someone else beat me to it LOL ... *
 
First, i am not an iTunes user, so I can't speak for it.
 
Second, what I would do is:
1. Back up all your music on a DVD or two.
2. Resize/create your partitions as you like, deleting as many music files as you need
3. Copy your music from your DVDs back to your computer to your shared hard drive.
 
Now, if you have 10GB of space *anywhere* on your drive, you probably don't need to do this. You can just resize whichever partition you need to so you have the space. If you are running OUT of space, you might consider clearing your HD a little.
 
Does this make sense?
 
In short, I wouldn't use iTunes to do the file-move. I am sure the program will be able to figure out where your media files are once you've moved them.
 
Lastly: iTunes may not be able to handle an ext3 partition. As such, you may consider using a Fat32 partition that is readable/writable by both Linux and Windows applications. Just a thought.

---

### Post by JohnJSal on 2006-08-05
Well, as of now I have no partitions, and I'd rather not have to mess with repartitioning later. I want to create all the partitions at the size I want when I install Ubuntu. I don't have a DVD burner, so I don't know how to backup my music. I would assume that the iPod itself is backing up everything on it, but I worry that deleting my music from my HD and then plugging in my iPod, instead of putting all my music back to the HD, will erase the contents of my iPod too and I'll be left with nothing.

---

### Post by JohnJSal on 2006-08-05
I just had a new thought. Since I plan to leave some extra space on my Windows partition anyway (and not shrink it down to the minimum, like 5GB), I can just repartition my HD as I want, then move my music over to the shared partition, delete the music from the Windows partition, and use that 10GB as the "padding" I wanted anyway (for updates, etc. and I still plan to install games directly to my Windows partition rather than the shared partition).

---

### Post by Steggy on 2006-08-05
If your iPod is big enough, you can use it to make sure you have a back up.

Now, I'm a little unsure of how easy or hard it is to actually pull must you have put on your iPod through iTunes back off the iPod. Last I knew, Apple was trying to make this as hard as possible, to stop people from sharing their music easily with others.

However, your iPod will also function as an external harddrive while it's plugged into your computer. Without using iTunes, you can simply drag-and-drop all your music from the folder on Windows to your iPod (accessing it through the icon that shows up in My Computer when your plug the iPod in.)

This will leave you with you're music still easily playable from the iPod, as well as easily accessable to Windows (as Windows will read it as just another USB harddrive.) However, this will take up approximately twice as much space on your iPod (though only until you copy the music from your iPod back to your shared partition, since then you can delete the extra copies.) If your iPod is big enough for that, you're all set.

If it's not big enough, you do have the option of removing all the music your currently have stored on it (through iTunes, I believe.) Then, copy the music back onto it through the Windows interface. You're music will then still be safely backed up; however, you won't be able to actually play it on your iPod, as I believe only music added through the iTunes interface can actually be played. Once you have the music successfully moved to your new shared partition, however, you can then use iTunes to copy the music (in playable form) back over to your iPod.)

---

### Post by JohnJSal on 2006-08-05
Well, problem solved (I hope). I went to Best Buy and bought an external HD, which I've been meaning to do for weeks now anyway. So this should help a lot!

---

### Post by em3raldxiii on 2006-08-05
LOL, uh, yeah ... that will definitely work haha.
 
But your other suggestion (moving the partitions about) would have worked just fine as well.

---

