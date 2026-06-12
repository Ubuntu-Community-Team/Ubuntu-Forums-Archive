---
title: "how to install a .bin file?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by cjfthistle on 2007-02-28
I found a thread on this topic and have tried the following in Terminal
> cjfthistle@dolcestilnovo:~/Desktop$ chmod a+x CM0102_REL.bin
cjfthistle@dolcestilnovo:~/Desktop$ ./CM0102_REL.bin
bash: ./CM0102_REL.bin: cannot execute binary file
cjfthistle@dolcestilnovo:~/Desktop$

I don't understand what's wrong.  I thought the chmod commond was to make the .bin file executable?

I have also tried right-clicking the file and udjusting the permissions section in properties so that I could execute it just by clicking on it, so what gives?

---

### Post by jvc26 on 2007-02-28
What are you trying to install?
Il

---

### Post by cjfthistle on 2007-02-28
It's a daft old computer game.  I have been experimenting with WINE and wanted to give CM01/02 a blast because I used to love it.

Now I have a .bin image of the disc (I must have the hard copy somewhere...) and don't know how to use it.

The game is Championship Manager 3, Season 01/02

---

### Post by jvc26 on 2007-02-28
If it works in WINE you might want to check out the gaming section of the forums here or on the wine set to see how/if you can run it :) 'fraid I hve little experience with WINE - decided to give things a go without using any windows apps.
Il

---

### Post by cjfthistle on 2007-02-28
Thanks anyway.  A prompt reply from the god of the Elves himself!

Wait a second....

Linux computer... getting Silmarillion references.... 

OH GOD!  I'M A GEEK!!

---

### Post by SSTwinrova on 2007-02-28
I don't think you're looking at a .bin file in the sense that most Linux users are used to (install executable). The fact that you said it was an image of the disc makes me think that you have the equivalent of an ISO:

[http://en.wikipedia.org/wiki/Disk_image#.BIN.2F.CUE](http://en.wikipedia.org/wiki/Disk_image#.BIN.2F.CUE)

Maybe try burning it onto a CD?

---

### Post by cjfthistle on 2007-02-28
I think you must be right.  I wish I had a cd burner...

Thanks for your help.

---

### Post by etyeow on 2008-05-06
I am a TOTAL BEGINNER migrating from Windows. I am also trying to install Google Earth. It has been downloaded onto my desktop as GoogleEarthLinux.bin

Can anyone please advise me on how to install the .bin file?  I am using Ubuntu 8.04 (kbuntu also).

Any response is deeply appreciated. Thank you.

E.T. Yeow

---

### Post by mkrahmeh on 2008-05-06
try using synoptic (or adept manager) instead, you can find them in 
k menu -> system -> adept/synaptic..theses package managers are more friendly to use than manual installations..

---

### Post by Titanape on 2008-05-20
> **etyeow said:**
> I am a TOTAL BEGINNER migrating from Windows. I am also trying to install Google Earth. It has been downloaded onto my desktop as GoogleEarthLinux.bin

Can anyone please advise me on how to install the .bin file?  I am using Ubuntu 8.04 (kbuntu also).

Any response is deeply appreciated. Thank you.

E.T. Yeow

I install a .bin the following way:

1. Open your Terminal

2. Change to the directory that the .bin was downloaded to.  example: ```
cd Desktop
```

3. To make sure you are in the same directory as your .bin  type ```
ls
```  That will display the files in your current directory.

4. Now that you are in the appropriate directory, type sudo chmod +x nameofthefile.bin.  That changes your bin to an executable file.

5. Finally, type ./nameofthefile.bin to run it.


Hope that helps.

---

### Post by nautaforever on 2008-05-23
> **Titanape said:**
> I install a .bin the following way:

1. Open your Terminal

2. Change to the directory that the .bin was downloaded to.  example: ```
cd Desktop
```

3. To make sure you are in the same directory as your .bin  type ```
ls
```  That will display the files in your current directory.

4. Now that you are in the appropriate directory, type sudo chmod +x nameofthefile.bin.  That changes your bin to an executable file.

5. Finally, type ./nameofthefile.bin to run it.


Hope that helps.


Thanks it was of great help 

what exactly does chmod do ?

Beginner to Ubuntu

---

### Post by giancast on 2008-05-24
Thanks Titanape, I had never installed a bin file and it worked perfectly. I am installing Real Player (which a try to avoid but I want to listen to the Detroit Pistons redio broadcasts. The station uses Real Player so I am stuck for the moment. Thanks again.

---

### Post by SidF on 2008-06-05
I'm completely new to Ubunutu 7.04 that came pre-installed on an eSys machine. I followed this thread to install RealPlayer11GOLD.bin ( to listen to radio on the BBC) and the installation asked me which folder to install in. Reading the books I have, I chose the opt folder and the installation seemed to complete. 
However when I try to run the app it says: Failed to execute child process "realplay" (No such file or directory)

I assume I made wrong choice? Can anyone suggest what I have to do the uninstall( if that is needed) or what I have to change to get RealPlayer working? Are there any other audio players that work with the BBC system?
Thanks in advance for any help
SidF

---

### Post by cairocalling on 2008-06-25
Thanks, Titanape. Very helpful. I had tried lots of other answers, without success.

---

### Post by sorolop on 2008-07-09
Hello i have a problem my self with bin files.
I want to edit some .bin files with C program language in order to read or write to those files.But  finaly can't open them to see my results.
Look the error report :

[B]Could not open the file /home/sorolop/Desktop/ptyxiakh/C/arxeio.txt.

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.[/B]
Character coding UTF-8


:) Thnks

---

### Post by thelugnut on 2008-07-09
A quick but sincere thanks to titanape.
Good job !

---

