---
title: "Playing Music on Edgy Eft stored on Windows 2000 PC"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by trebor7_1 on 2007-02-10
I am trying to play FLAC / MP3 stored on a Windows 2000 box on my network.
If I drag a file to the local Ubuntu PC then it plays ok with Totem or Rhythmbox. 
What I'd like to do is just point at the file and have it play as I can with other windows boxes.
I have the windows folder with music in mounted on the Ubuntu desktop but cant get anything to play.
Have I missed something here.
Thanks for any help or suggestions.

Regards

Trebor

---

### Post by jpeddicord on 2007-02-10
Go to Applications > Add/Remove. Search for "mp3". The second result should be "GStreamer Extra Plugins," check it if it's available. Hit OK, and the support for MP3 and others will be available within minutes.

If GStreamer Extra Plugins is not available, then go to System > Administration > Software Sources. There should be five boxes on the window that comes up (after you enter your password, anyway). Make sure all of them are checked, then close the window and Reload if it asks. Then try the steps above, and if Add/Remove needs reloaded, reload that too. :) 

See the attached screenshots for more info.

Jacob

---

### Post by trebor7_1 on 2007-02-10
Jacob, thanks but the MP3 or FLAC will play fine if its stored locally omn the Ubuntu box. The problem is clicking on a file stored on a windows 2000 box across the network. That file will not play.
This will work ok with 2 windows boxes. just trying to do the same with Ubuntu

---

### Post by question_chick on 2007-02-10
Do you have the right permissions to access the files?

It could be that you don't have enough permissions set up to play the files.

---

### Post by risbac on 2007-02-10
Ok, seems to be a known bug with Edgy ([http://bugzilla.gnome.org/show_bug.cgi?id=359133](http://bugzilla.gnome.org/show_bug.cgi?id=359133))
It could be a lack of rights on the shared files also. But as you can copy them to your desktop, you seem to have enough rights.

so two solutions:
-wait for the bug to be fixed (but when, good question, could be very fast but also take some weeks...)
-use a software to share your music? If you use Itunes on the main computer for instance, then Banshee and probably Rhymthbox will see the computer without anything to set.

---

### Post by trebor7_1 on 2007-02-10
risbac, I checked the link and that looks like the problem, I dont use iTunes this is just a folder with lots of FLAC's in.
question_chick the permissions look the same in the network mounted folder and on the desktop so dont think thats the problem...

---

### Post by risbac on 2007-02-11
Ok then it must be this bug... On the link I gave you, there is no fix, so I guess you have to wait if you want to use the shared folder.

If the computer containing the FLACs is always on, you could maybe try to mount the folder locally. But I don't think it would work. Still worth a try if you do not have any other solution.

---

### Post by trebor7_1 on 2007-02-11
I do have the folder sitting on my Ubuntu desktop with a connection wire icon and small smb label so I think thats "mounted locally" sadly still the same result. Thanks for the suggestion though. looks like I have to wait for the fix, :-(

---

### Post by risbac on 2007-02-11
>  	I do have the folder sitting on my Ubuntu desktop with a connection wire icon and small smb label so I think thats "mounted locally" 

By "mounted locally", I meant in the file system of your computer. It would then appear like a regular folder, you can't see it's on the network. You can do this by adding the folder in the /etc/fstab file. But sometimes it will slow down the whole computer if it's not stable, I had this problem at work. So maybe it's worth a try, but I'm not sure it will be that efficient. It has its advantages though. You can then use any music jukebox to manage the songs even if they are not on the computer itself.

---

### Post by trebor7_1 on 2007-02-11
Hmmm not too sure how to do that. I used connect to server to get the folder as a network folder. 
Looking in fstab what would be the format to mount the folder from there ?

---

