---
title: "Making a random smartlist with a dvd's worth of music in Amarok ?"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-04-28
In Windows, I use Media Center (11) in order to create a 'smartlist', that I use to fill my 2 gig memory card for my Sony Ericsson W810i walkman phone. Similarly, I'd like to make a data DVD of random shuffled Mp3 files for playback on my DVD player, but I don't see this option available through Amarok. 

Am I just missing where it is, or does it not exist ?  Of course I can just drop random folders, but the point of the randomly shuffled playlist, is that I have nothing to do with the selection process, which is what makes the list unique. So, is it possible to have Amarok create a random smartlist filled with 4.7 gigs worth of shuffled Mp3's ?  And if not, is there a program I can use in order to achieve this result ?

Doug

---

### Post by Sweet Spot on 2007-05-01
Is it that nobody saw this thread, or is there simply no application made for this task in Ubuntu/Linux ?

---

### Post by klytu on 2007-05-02
> **Sweet Spot said:**
> Is it that nobody saw this thread, or is there simply no application made for this task in Ubuntu/Linux ?

I saw the thread but I also couldn't figure out how to do this with Amarok. My first thought was that even if there is no specific application that will do what you want, it shouldn't be too difficult to write a script to solve your problem. A bit of searching turned up a number of people who have already created such a script. [[COLOR="Red"]_**Here is a link to one such script written in Python. **_[/COLOR]]("http://www.linuxgangster.org/modules.php?name=Content&file=viewarticle&id=30") I think you would be able to modify it to your needs without much difficulty. For example, in the script you could just substitute the appropriate directories for your own source and target directories and  set num_max to about 1100-1200 for approximately 4.7GBs worth of mp3s assuming each one averages about 4MBs. If you are not sure how to use the script, you can do this from a terminal: ```
gedit random_playlist
``` then cut and paste this:> #!/usr/bin/env python
#
# Random playlist
#
# Python script to copy files randomly from one directory to another.
# I made this to randomly generate a playlist for my MP3 player.
#
import os
import random
from shutil import copyfile
sourcedir = "directory where your mp3 files live"
targetdir = "your playlist directory"
files = os.listdir(sourcedir)                   # List of files
num_files = len(files)                          # Number of files
file_list = []                                  # Initiates random playlist
num_max = 50                                    # Number of files to copy
print "Processing " + str(num_files) + " files"
for i in range(0,num_max):
	index = random.randrange(0, num_files, 1)
	file_list.append(files[index])
for file in file_list:
	try:
	# print "Copying " + sourcedir + "/" + file + " to " + targetdir + "/" + file
		copyfile(sourcedir + "/" + file, targetdir + "/" + file)
	except:
		print "Unable to copy file"
print "Done..." Edit the sourcedir, targetdir, and num_max lines for your needs and save the file. Then do: ```
chmod +x random_playlist
``` and then: ```
./random_playlist
``` and you will have a random list of mp3s in the targetdir you placed in the script - you can burn these to a disk.

---

### Post by klytu on 2007-05-02
In my post above, the correct indentation doesn't show. If you don't know what I mean, just download the attachment to this post to your home directory, rename it to remove the .txt extension, open it with gedit or your favorite text editor and follow my post above. You might want to initially try a small number for num_max to confirm the script does what you want and to see how long it takes to run.

---

### Post by Sweet Spot on 2007-05-02
Thank you Klytu, I really appreciate your efforts. I have to say though, that I find it a bit (I guess) weird that this sort of application hasn't been sought after more than it would appear to have been. I mean, that's the only way I can word what it seems like, without saying something to the effect of : " Yeah sure, every Windows application has its equivalent in Linux/Ubuntu, riiiight". 

I guess I'm saying that because I feel a bit cheesy now, after having given a speech in my effective speaking class yesterday, which was a speech to persuade, and my topic was why people should use Linux Vs. Windows. A big part of the argument, was that it is easy to find pretty much any application in Linux, which a person might have been using in Windows etc...  That's irony for you eh ?

Now, I'm not saying that the solution you've presented isn't viable, it's just that a noob might find it discouraging to have to delve into such a thing compared to a simple GUI based app with its own editing scheme/wizard, if you will.  I also can't help but think that there's got to be another program out there which can perform said tasks. In the meantime, I'll have a go at this one, and I DO thank you very much. 

Doug

---

### Post by klytu on 2007-05-02
> Thank you Klytu, I really appreciate your efforts. I have to say though, that I find it a bit (I guess) weird that this sort of application hasn't been sought after more than it would appear to have been. I mean, that's the only way I can word what it seems like, without saying something to the effect of : " Yeah sure, every Windows application has its equivalent in Linux/Ubuntu, riiiight". 

I understand what you mean, but bear in mind that there is a distinction between Open Source Software and Ubuntu/Debian/GNU-Linux. Windows Media Player, for example, is a proprietary piece of software that runs only (as far as I know) under the Windows operating system. Mozilla-Firefox, for example, is Open Source Software that runs under both Windows and Ubuntu. 

There are several open source programs that duplicate features of Windows Media Player; many of those programs have MORE features. Mplayer is the first software that comes to mind as an example.  Amarok focuses on different ways to enjoy music and I think it does this very well. In fact, there may well be a method of combining its smart playlist and dynamic playlist features to do exactly what you want - although I haven't figured out how myself. 

>  I guess I'm saying that because I feel a bit cheesy now, after having given a speech in my effective speaking class yesterday, which was a speech to persuade, and my topic was why people should use Linux Vs. Windows. A big part of the argument, was that it is easy to find pretty much any application in Linux, which a person might have been using in Windows etc...   Did you include in your argument ideas about security, efficient use of resources, and the fact that Ubuntu doesn't charge users licensing fees?

>   I DO thank you very much.  You're welcome! :-)

---

### Post by Sweet Spot on 2007-05-02
> **klytu said:**
> 
 Did you include in your argument ideas about security, efficient use of resources, and the fact that Ubuntu doesn't charge users licensing fees?



I'm surprised that felt the need to ask that  ! But of course my good fellow... Without such points in the speech, it would have been just another rant which nobody should have cared about. And seeing as how these issues you raise should be a major concern to college students, leaving that out would be a crime.

---

