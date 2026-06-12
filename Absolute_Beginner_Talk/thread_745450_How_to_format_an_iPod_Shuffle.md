---
title: "How to format an iPod Shuffle"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Berean on 2008-04-04
Hi, 

I have another thread going concerning using an iPod Shuffle.  Everytime I mount and unmount it a folder appears - despite deleting it on numerous occasions - that I assume is a control folder to stop me from using the iPod in Linux.  Therefore, I want to format the horrible little thing and get rid of all of Apple's nasties.  How do I do it?  Using gparted it doesn't seem to recognise it.  Can I do it in terminal?  It's mounted as media/IPOD.  Once I've formatted it I can follow the other thread.  Many thanks.

---

### Post by neurostu on 2008-04-04
Do you want to be able to use the ipod to play music? If you do you cannot get rid of the control folder, it contains a database file that the ipod reads to play your music.

I have a 2gb shuffle and here is a thread I started about using it in ubuntu.
[http://ubuntuforums.org/showthread.php?t=717626](http://ubuntuforums.org/showthread.php?t=717626)

---

### Post by Berean on 2008-04-05
Thank you.  I'm going to give it a try.  Will let you know.  Regards,

---

### Post by Berean on 2008-04-07
Neurostu,

I can't get Python installed, so what hope do I have of following your thread?  Don't ask me why!  I've  downloaded your exe file, but I can't get it to run.  Any ideas?  Regards,

---

### Post by neurostu on 2008-04-07
You shouldn't be using anything with an exe. I'm not sure what exe your talking about.

It is really easy to get this script working. To install python all you need to do is type:

```

sudo apt-get install python

```
download the python script, it should be something like script.py ( <-- notice the .py file type)
Then open a terminal, cd to shuffle (you must have the script on the shuffle in the lowerst directory) then type:
```

python rebuilddb.py (where rebuilddb.py is the name of the script)

```

Try that then let me know what happens.

---

### Post by Berean on 2008-04-07
> **neurostu said:**
> You shouldn't be using anything with an exe. I'm not sure what exe your talking about.

It is really easy to get this script working. To install python all you need to do is type:

```

sudo apt-get install python

```
download the python script, it should be something like script.py ( <-- notice the .py file type)
Then open a terminal, cd to shuffle (you must have the script on the shuffle in the lowerst directory) then type:
```

python rebuilddb.py (where rebuilddb.py is the name of the script)

```

Try that then let me know what happens.

neurostu,

thanks for your persistence!  I might have misunderstood, but I tried doing this in Ubuntu and failed - the iPod reset the directory called iPod Control (I think) after I had deleted it and I continued to be unable to do anything.  So, I thought I would need to do it in Windows - specifically Vista - but Python wouldn't download.  Each time I try something with the iPod it stops my wife from listening to it.  To be clear, I've downloaded the file "rebuild_db" which is now sitting on my Ubuntu desktop.  You've stated in your iPod thread that I should download the rebuild_db into the iPod: do you mean into the iPod Control folder, or simply into the iPod so as soon as you open the iPod it's there?  I've got the newest version of Python so had nothing to download.  Is this all correct so far?  Thanks again for persevering with me!  Kind regards,

PS If I double click on the file on the desktop it opens to reveal 5 files, one of which is an exe file.

---

### Post by neurostu on 2008-04-07
Ok so if you open the archive file that you download it will contain the following files:
```

License.txt
Readme.txt
rebuild_db-win32.src.zip
rebuild_db.exe
rebuild_db.py   <----- COPY THIS FILE

```
The EXE file is for windows, you will NEVER use a .exe file in linux. So unless you are using wine or crossover you can forget about .exe meaning execute.

When you plug in your ipod it will appear on your desktop. Double click on the icon and add the **rebuild_db.py ** file to THAT directory. This is one directory down from the IPOD CONTROL directory. Infact the IPOD CONTROL and the rebuild_db.py will be contained in the same folder.

Then put all the music you want on your ipod into the ipod. You can put it into the ipod control dir or you can create your own dir (this is what I did)


Then in a termial CD to your ipod directory.  then run the following command:
```

python rebuild_db.py

```

The script will then search the ipod for all MP3s and rebuild the ipod database so you can then play the files.

Let me know how that goes.

---

### Post by Berean on 2008-04-08
Aargh!  This is a screen shot of what happens when I CD to "LOU'S IPOD" which is on the Desktop.  At the prompt, I CD /home/ian/Desktop and then - when there - I CD to LOU'S IPOD!  But I can't get any further.  Python says I have the most up to date version installed. But nothing is happening, and the text file is empty.  The last screen shot is of LOU'S IPOD but I can't delete both text files because it says I don't have permission.  Am I really being so stupid, or am I having a problem with my system?  Many thanks.

---

### Post by Berean on 2008-04-08
I've just realised the directory is actually /media/LOU'S IPOD but that gives me just the same response.

---

### Post by scramasax on 2008-04-08
> **Berean said:**
> Hi, 

I have another thread going concerning using an iPod Shuffle.  Everytime I mount and unmount it a folder appears ....

Yeah, it would be hidden under OS X -- unless you looked at the device from the command line:

[http://rixstep.com/2/20050321,00.shtml](http://rixstep.com/2/20050321,00.shtml)

The same goes for Windows.  One assumes that this is the price Apple must pay to get cooperation from the record labels -- because that's where the music is stored.  Not that hiding it with Finder flags and suchlike is anything more than a speed-bump to anyone who wants to copy music on and off for nefarious -- or genuine -- reasons.

However, didn't you look at the documentation Ubuntu has on using an iPod with Ubuntu?

[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

Does gtkpod not work satisfactorily for you?  It should be in the Repositories.

---

### Post by neurostu on 2008-04-08
Scramasax,  He is working with the new ipod shuffle which has some problems getting recognized under gtkpod. 

berean:  I noticed that you are placing files of type .OGG into your ipod. The ipod does not support .OGG files.  Only .AAC and .MP3.

Make sure your audio files are in  .mp3 format.

when you open a terminal and then cd to your ipod type the following command:
```

ls -all

```
and then paste that here, it will let me know if you are in the correct dir

---

### Post by Berean on 2008-04-08
> **scramasax said:**
> Yeah, it would be hidden under OS X -- unless you looked at the device from the command line:

[http://rixstep.com/2/20050321,00.shtml](http://rixstep.com/2/20050321,00.shtml)

The same goes for Windows.  One assumes that this is the price Apple must pay to get cooperation from the record labels -- because that's where the music is stored.  Not that hiding it with Finder flags and suchlike is anything more than a speed-bump to anyone who wants to copy music on and off for nefarious -- or genuine -- reasons.

However, didn't you look at the documentation Ubuntu has on using an iPod with Ubuntu?

[https://help.ubuntu.com/community/PortableDevices/iPod](https://help.ubuntu.com/community/PortableDevices/iPod)

Does gtkpod not work satisfactorily for you?  It should be in the Repositories.

Unfortunately, not!  I'm slowly being worn down by Apple, but I'm going to persevere.  Thanks.

---

### Post by Berean on 2008-04-08
I'm spending too much time on this issue at present, so will come back to it in a couple of days when I'm less stressed and tired.  Thanks so far, and I will post soon.  Thank you.  Berean

---

