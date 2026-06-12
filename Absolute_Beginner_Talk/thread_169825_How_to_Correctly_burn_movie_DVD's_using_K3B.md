---
title: "How to Correctly burn movie DVD's using K3B"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by user1397 on 2006-05-03
I have some videos in avi format that i converted to dvd format using avidemux. 
Now i want to use K3B to burn these videos to dvd+r's so that i can watch them on my tv.  what do i do? (in K3B)

---

### Post by user1397 on 2006-05-03
*Bump!*

---

### Post by user1397 on 2006-05-03
I just got to: BUMP!

---

### Post by Digidiz on 2006-05-03
no create a video_ts folder if not already created
 
wait k3burner has the option to burn dvd movies?? if so drag all ya files into the video_ts folder on the k3b burner software then simply just burn hence the BUMP easy aint it??

---

### Post by user1397 on 2006-05-03
well see i tried that exact procedure, but my dvd player says "unknown disc"
?????????????????????????????????????????????????????????????????

---

### Post by user1397 on 2006-05-03
What actually happens, is:
In K3b, i go to new>new video dvd project
i add my mpeg movie to the video_ts folder (i don't have an audio file for the corresponding audio_ts folder), i click burn, and it says:
"Found files to be bigger than 2GB. These files will only be accessible if mounted with UDF."
"Enabling UDF extension."
"Could not determine size of resulting image file."
Error

---

### Post by halitech on 2006-05-03
I use the info found here minus creating the iso and use k3b to create the video dvd project. it breaks it down to 3 or 4 .vob files and burns without a problem.

[http://smorgasbord.net/node/166]("http://smorgasbord.net/node/166")

---

### Post by Digidiz on 2006-05-04
[quote=erik1397]What actually happens, is:
In K3b, i go to new>new video dvd project
i add my mpeg movie to the video_ts folder (i don't have an audio file for the corresponding audio_ts folder), i click burn, and it says:
"Found files to be bigger than 2GB. These files will only be accessible if mounted with UDF."
"Enabling UDF extension."
"Could not determine size of resulting image file."
Error[/quote]
 
[quote=Ramses de Norre]sudo chmod xxx path_to_file
The first x are the permissions for the owner, the second for the owner's group, the third for anybody else.
1=x (executable)
2=w (writable)
4=r (readable)
And just add the numbers of the permissions you want to give.[/quote]
 
[quote=Ramses de Norre]You did the sudo chmod 666 file_name ?
What's the output of ls -a for that file?
 
Reading your first post again, I guess you should edit it using sudo. Do sudo gedit file_name and type in your user password.[/quote]
 
[quote=erik1397]I just got to: BUMP![/quote]
 
 
 
dont you know that dvd format is .vob .bup etc.... and not .avi .mpg etc.. ???

---

### Post by user1397 on 2006-05-04
[quote=Digidiz]dont you know that dvd format is .vob .bup etc.... and not .avi .mpg etc.. ???[/quote]
Hmmm well how would you do that then? I encoded my movie files with avidemux using the auto>dvd movie option.  It became mpeg instead of avi!

---

### Post by nalmeth on 2006-05-04
have you tried [devede?]("http://www.rastersoft.com/programas/devede.html")

---

### Post by user1397 on 2006-05-04
[quote=nalmeth]have you tried [devede?]("http://www.rastersoft.com/programas/devede.html")[/quote]
I don't see it anywhere on synaptic, and i have the automatix repos...

---

### Post by nalmeth on 2006-05-04
Follow download links on the site I linked.
You'll figure it out
I have yet to do anything with it, but have heard good things. Was pleased with the GUI

---

### Post by openmind on 2006-05-04
Alright, I had ***Exactly*** the same problem not too long ago, and figured out a foolproof way to do it (My favorite way!:D). I'm not saying it's the easiest/best/preferred way, all I know is it works, so I've stuck with it!

1. Get [tovid]("http://tovid.berlios.de/en/index.html") 

2. Open tovid, click "add menu", click "add video" and choose your avi. Make sure the options are ok, and click "2. Encode" (at the top) Then "start encoding" (at the bottom).

This process takes a long time, as it's converting avi to good mpg. The file will grow about three times bigger than the avi was.

3. When it gets to "file ready to burn", I guess you could, but I don't. take the following script, make it executable and put it in your $PATH somewhere (I put in /usr/bin).
 ```
#!/bin/bash
#Make iso from MPG's

dvdauthor -o dvd -t $1 &&
dvdauthor -o dvd -T &&
mkisofs -dvd-video -o dvd.iso dvd/ &&
exit
``` 
I named it "mkiso" as that is what it does, it makes an ISO (Image) fom the MPG.

4. In a terminal type;
```
$ mkiso "Name of mpg".mpg
``` 
5. When it's done you should have a "dvd.iso" in the folder that the MPG is in, open k3b, click "tools" then "Burn iso to DVD" and you'll have your movie on DVD, pop it into your player and it'll start playing on your TV!

Like I say, I'm sure more experienced people here will giggle, or have a better way but this way works for me every time.

Good Luck! Any problems come back.:D

---

### Post by user1397 on 2006-05-04
[quote=openmind]Alright, I had ***Exactly*** the same problem not too long ago, and figured out a foolproof way to do it (My favorite way!:D). I'm not saying it's the easiest/best/preferred way, all I know is it works, so I've stuck with it!

1. Get [tovid]("http://tovid.berlios.de/en/index.html") 

2. Open tovid, click "add menu", click "add video" and choose your avi. Make sure the options are ok, and click "2. Encode" (at the top) Then "start encoding" (at the bottom).

This process takes a long time, as it's converting avi to good mpg. The file will grow about three times bigger than the avi was.

3. When it gets to "file ready to burn", I guess you could, but I don't. take the following script, make it executable and put it in your $PATH somewhere (I put in /usr/bin).
 ```
#!/bin/bash
#Make iso from MPG's

dvdauthor -o dvd -t $1 &&
dvdauthor -o dvd -T &&
mkisofs -dvd-video -o dvd.iso dvd/ &&
exit
``` 
I named it "mkiso" as that is what it does, it makes an ISO (Image) fom the MPG.

4. In a terminal type;
```
$ mkiso "Name of mpg".mpg
``` 
5. When it's done you should have a "dvd.iso" in the folder that the MPG is in, open k3b, click "tools" then "Burn iso to DVD" and you'll have your movie on DVD, pop it into your player and it'll start playing on your TV!

Like I say, I'm sure more experienced people here will giggle, or have a better way but this way works for me every time.

Good Luck! Any problems come back.:D[/quote]
I'll try this tomorrow, too tired to do it now.  Hope it works and if it does i'll post back the results!

---

### Post by user1397 on 2006-05-09
Thanks openmind! Your procedure worked flawlessly!
Just for beginners, however, i would like to add to step 3 that you need to make a new file in gedit, (application->accessories->text editor), paste the commands in step 3 into the new file, save, close it, and then right-click on it ->properties->permissions, and select executable(all 3) After that, put it in /usr/bin.  You need root permissions for this, so you can press Alt+F2, then type in 
gksudo nautilus
press enter, and then browse to your /usr/bin folder and move the step 3 file into /usr/bin.

---

### Post by openmind on 2006-05-09
You're Welcome Erik, and thanks for the addition for Complete beginners!

I think we've got it covered now:D

---

### Post by babwe on 2006-05-09
just do a data copy in k3b, and if your dvdplayer can play vob. mpeg etc it will popup as a menu on telly, and then click that file m8

---

### Post by user1397 on 2006-05-09
[quote=babwe]just do a data copy in k3b, and if your dvdplayer can play vob. mpeg etc it will popup as a menu on telly, and then click that file m8[/quote]
i tried that- a lot of times, and it never worked. openmind's way is fullproof and will always work, so i'm sticking to it :cool:

---

### Post by user1397 on 2006-05-09
[quote=openmind]You're Welcome Erik, and thanks for the addition for Complete beginners!

I think we've got it covered now:D[/quote]
Yep, i think we do :D

---

### Post by uzi09 on 2006-07-06
kinda long though, if someone knows a thing or two about shell scripting, is it possible to automate this? (or atleast a majority of it?)

---

### Post by user1397 on 2006-07-06
[quote=uzi09]kinda long though, if someone knows a thing or two about shell scripting, is it possible to automate this? (or atleast a majority of it?)[/quote]well, the official tovid website has a tutorial on how to do all of this through the command line, but my guide is just for point and click-oriented "newbies".  here's the command line guide: [http://tovid.wikia.com/wiki/Using_the_tovid_command-line](http://tovid.wikia.com/wiki/Using_the_tovid_command-line) or [http://tovid.wikia.com/wiki/How_to_make_a_basic_DVD](http://tovid.wikia.com/wiki/How_to_make_a_basic_DVD)

---

### Post by uzi09 on 2006-07-08
it worked for me quite well, but i must admit, it could not compete with the one i've created with nero before.

now before the flame war starts -- i'm not saying that one program is better than another or anything, nor am i saying that these freeware programs should be competing with a group of people getting payed a lotta money for makin that program (although this does happen often).

it's just, i never got a chance to sitdown and make any chapters or title pages or anything like that.

haven't tried devede yet either, i think i might do that this time around (was kind of under a stict deadline for the last one, so wasn't able to put enough time/effort in it either).

---

### Post by user1397 on 2006-07-08
whatever floats your boat

---

### Post by user1397 on 2006-07-12
btw, i have made a guide in the howto forum based on this thread, but way more updated: [Howto: Make Dvd Videos From An Avi File]("http://www.ubuntuforums.org/showthread.php?t=183936")

---

### Post by unwoken on 2006-07-14
i'm having a strange problem with the script suggested by openmind.

every time i run the command to make the iso, it creates an iso, but one which has all the previous files i used to creat iso's with inside it (as seperate chapters).  the most recent iso it made has four seperate shows in it, and i specifically stated the exact path and file i wanted (only one) when i entered the command into the terminal.

the iso is also obviously getting bigger every time.  can anyone tell me how i can just create an iso with a file i choose and not all previous ones too??

just FYI i am using ubuntu, and do not have tovid.  i created the mpg using avidemux (auto dvd option) and burnt the iso onto disk using k3b.

hopefully someone can help.

cheers,

u.

---

### Post by user1397 on 2006-07-15
> **unwoken said:**
> i'm having a strange problem with the script suggested by openmind.

every time i run the command to make the iso, it creates an iso, but one which has all the previous files i used to creat iso's with inside it (as seperate chapters).  the most recent iso it made has four seperate shows in it, and i specifically stated the exact path and file i wanted (only one) when i entered the command into the terminal.

the iso is also obviously getting bigger every time.  can anyone tell me how i can just create an iso with a file i choose and not all previous ones too??

just FYI i am using ubuntu, and do not have tovid.  i created the mpg using avidemux (auto dvd option) and burnt the iso onto disk using k3b.

hopefully someone can help.

cheers,

u.well maybe you should follow the guide i just mentioned a post earlier, that might work for you

---

### Post by chollis888 on 2006-07-15
Hey guys how's it going?  Well I can say that I've tried both methods mentioned here and although the script works great no complaints plan to use it when I need to. But [Devede]("http://www.rastersoft.com/programas/devede.html") works great also, it has the same outcome  but with much less effort. All you have to do is download the tar.bz2 file from the link at the bottom of the web site, extract it to home folder cd to it with a:
```
cd devede
``` and then do a:
```
sudo ./install.sh
``` 
I'm running Dapper and this worked perfect the first time for me. It installed the desktop link in application>sound & video>devede.

The gui could'nt be easier, it does all the encoding and makes the .iso for you and it also deletes those temp files or leaves them if you prefer.

I read someone was having problems with the old conversions ending up on his newest project with tovid, thats because your leaving the old files in your output dir. Delete those and your temp files before you start a new project that should fix it.

one last thing Devede uses mencoder to encode so anything you can play on mplayer can be converted to mpg. I encoded .divx 6.2 without a problem. It has the same dependencies as Tovid, so you should already have everything you need if your using Tovid. So tweakout mplayer codecs and enjoy.

I had a 1hr41min encode time for a 2hr12min movie form .avi to dvd.iso, I'm not sure I have a reason to ever boot up windows xp again. I believe this was my last hurdle but I'll have to wait and see..:mrgreen:

One last thing it told me I was using 115% of the dvd-r but I ran it anyway and the dvd.iso only ended up being 1.9gigs i believe thats thanks to mkisofs. So pay that disk usage bar nomind however it did need 11gigs of free space to acomplish this so be sure you have plenty of free space. And as mentioned before it will remove those extra tmp files that it makes.:KS

---

### Post by user1397 on 2006-07-16
> **chollis888 said:**
> Hey guys how's it going?  Well I can say that I've tried both methods mentioned here and although the script works great no complaints plan to use it when I need to. But [Devede]("http://www.rastersoft.com/programas/devede.html") works great also, it has the same outcome  but with much less effort. All you have to do is download the tar.bz2 file from the link at the bottom of the web site, extract it to home folder cd to it with a:
```
cd devede
``` and then do a:
```
sudo ./install.sh
``` 
I'm running Dapper and this worked perfect the first time for me. It installed the desktop link in application>sound & video>devede.

The gui could'nt be easier, it does all the encoding and makes the .iso for you and it also deletes those temp files or leaves them if you prefer.

I read someone was having problems with the old conversions ending up on his newest project with tovid, thats because your leaving the old files in your output dir. Delete those and your temp files before you start a new project that should fix it.

one last thing Devede uses mencoder to encode so anything you can play on mplayer can be converted to mpg. I encoded .divx 6.2 without a problem. It has the same dependencies as Tovid, so you should already have everything you need if your using Tovid. So tweakout mplayer codecs and enjoy.

I had a 1hr41min encode time for a 2hr12min movie form .avi to dvd.iso, I'm not sure I have a reason to ever boot up windows xp again. I believe this was my last hurdle but I'll have to wait and see..:mrgreen:

One last thing it told me I was using 115% of the dvd-r but I ran it anyway and the dvd.iso only ended up being 1.9gigs i believe thats thanks to mkisofs. So pay that disk usage bar nomind however it did need 11gigs of free space to acomplish this so be sure you have plenty of free space. And as mentioned before it will remove those extra tmp files that it makes.:KS
wow, i have to say im impressed, i will look into devede more

---

### Post by unwoken on 2006-07-16
> **chollis888 said:**
> 

I read someone was having problems with the old conversions ending up on his newest project with tovid, thats because your leaving the old files in your output dir. Delete those and your temp files before you start a new project that should fix it.



**@erik1397**

Thanks for your reply that i should follow your thread, but the only difference between what i did and your thread was create the mpg using avidemux which is not the problem.  the mpg i created is fine.

it was creating the iso which caused the problem, which I did using exactly the same script as you have in your thread.

...

**@chollis888**

Thank you, that seems to be my problem exactly.  I think i will have a go at using devede as you suggested, but i have a question wihch hopefully you can answer.

Can you tell me where i delete the temp files from?

Also, when you mention that I left the old files in the 'output dir', can you tell me what you mean?  The files which appear in the final iso *are* in the same tree struture (about 3 directories away), but not actually in the same directory.  Do i have to isolate it further?


I would like to have a go using devede, but if you could answer my query that would be fantastic! 

u.

---

### Post by chollis888 on 2006-07-17
> 
**[B]@chollis888**
 
Thank you, that seems to be my problem exactly. I think i will have a go at using devede as you suggested, but i have a question wihch hopefully you can answer.
 
Can you tell me where i delete the temp files from?
 
Also, when you mention that I left the old files in the 'output dir', can you tell me what you mean? The files which appear in the final iso *are* in the same tree struture (about 3 directories away), but not actually in the same directory. Do i have to isolate it further?
 
 
I would like to have a go using devede, but if you could answer my query that would be fantastic! 
 
[/B]
 
 
**Ok, well since your using dvdauthor in that script it's putting the temp files in dvdauthor's default workdir. which I believe is /tmp and that is also the system temp folder. So the problem is'nt your script but dvdauthor. **
**You can change dvdauthor's default workdir. I'm at work now, so I'm using windows and can't be positive, but I'll give this my best.**
**Go to your home folder and hit ctrl-h, that will show you all your hidden files. Look for a .dvdauthor folder. Inside that you should see a preferences txt doc, open that with any text editor, you should'nt need any special permissions to write to it since it's in your home folder. change the wrkingdir= to any folder in your home folder. You could for instace in terminal do a:**
```

**mkdir ~/temp **

```
 
**That should create a folder called temp in your home dir. Then just redirect dvdauthor to that folder.**
**Or what I believe I did was make a file called .dvdauthorrc. To do this just type in terminal:**
```

**gedit ~/.dvdauthorrc**

```
 
**and then in the empty file type:**
```

**WORKDIR=temp **

```
 
**And then save it (crtl-s). Now you should be able to manually move the contents of /home/yourusername/temp to the trash when your done with the files.**
**I would love to be 100% sure about this, but, as I said, I'm at work on windows and can't double check. I will as soon as I get home.**
**You can also double check by going to the "/usr/share/doc/dvdauthor" folder. Just read thru it until you find how to change the WORKDIR. Hope that helps and goodluck. **
 
**O yea, dont worry about deleating files in output dir. after futher thought the deletion of the workdir files should fix this. To verify this is truley your problem, look in /tmp thats the default workdir of dvdauthor and the files you see in your .iso will also be there.**
**And do look into Devede it takes all of 10secs to have up and running. I downloaded it in under a min on dailup:mrgreen:. I even sent the author a E-mail to thank him, best program of the type I ever used.**
**Also I need to say thanks to nalmeth for the suggestion:KS . I can't believe he knew about this and never tried it for himself. It was so cool I went thru my entire 160gigs of movies trying to find different formats to test it out. Not a problem yet. **
**And if anyone is interested, I can post a link to some cool nautilus scripts to mount and unmount .Iso's, and get this .Nrg's also, with just a right click on the file. **[Click here for scripts.]("http://doc.gwos.org/index.php/Mount_ISO_script")

---

### Post by unwoken on 2006-07-18
thanks chollis888.

i will check this out tonight when i go home (also now at work on windows).  That's fantastic though!  Really appreciate the help.

u.

---

### Post by chollis888 on 2006-07-18
> BTW, if you have an old HDD that you use for generating dvd images,
you can create /usr/local/etc/dvdauthor.conf or ~/.dvdauthorrc and add
the line:

    WORKDIR=foo

Then you won't need to specify -o to dvddirgen or dvdauthor.
Alternatively, you could just set

    WORKDIR=mydvd

to always have it create a DVD in the current working directory.

 
Sorry man I was way off, this what I was talking about though. And that temp folder does'nt get flushed on reboot.  I just started up the Qdvdauthor gui and got a message , telling me that a file in  /tmp  had exceeded the set time limit.    Hope you double checked me. But anyways, I made a file named it ".dvdauthorrc" and put it in my home folder. In the emtpy file I put WORKDIR=dvd. And then created a folder and named it dvd in home also. Now that working dir is your problem. The script is putting everything in dvdauthor's working dir in the iso. So point that to a good location and delete the contents manually. Goodluck.

---

### Post by Koppie on 2007-07-18
I tried both and found devede way easier as well.  Not only is it way easier to install--it's in the Gutsy repo so it only took a single command--but I got errors with tovid.  Not worth troubleshooting when there's another program that works.  (One thing: I didn't see any options for creating a menu with devede so if you need that feature then this program might not be sufficient.)

--Koppie

---

### Post by user1397 on 2007-07-18
> **Koppie said:**
> I tried both and found devede way easier as well.  Not only is it way easier to install--it's in the Gutsy repo so it only took a single command--but I got errors with tovid.  Not worth troubleshooting when there's another program that works.  (One thing: I didn't see any options for creating a menu with devede so if you need that feature then this program might not be sufficient.)

--KoppieYep, that is true.  Devede might be easier to install for ubuntu users, but it does not have the abundance of features of tovid.  Pick whichever one suits your tastes.

---

