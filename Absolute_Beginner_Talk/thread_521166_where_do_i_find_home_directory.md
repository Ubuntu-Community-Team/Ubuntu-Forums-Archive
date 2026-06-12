---
title: "where do i find home directory"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by nikef on 2007-08-09
hi i am trying to copy a file to the home directory from a flash usb
how can i do this please

thanks

[COLOR="Red"]this is now solved,i have my wireless belkin adapter running now,my problem was solved because i have 2 belkin adapters and was using the wrong on[COLOR="Red"]e[/COLOR],as soon as i plugged it in,the light started flashing,i knew the this was going to work[/COLOR] :):):):)  :guitar:

---

### Post by kostkon on 2007-08-09
Sorry to say this but I would like to ask you to rephrase your question a little. For me personally, it is difficult to figure out what you want to say.

---

### Post by nikef on 2007-08-09
> **kostkon said:**
> Sorry to say this but I would like to ask you to rephrase your question a little. For me personally, it is difficult to figure out what you want to say.

yeah sorry for not explaining properly
i have just copied the drivers for my belkin adaptor on to my flash disc
these are the instructions i am trying to follow 

[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

i have put my flash disc on to the ubuntu pc a box has came up showing me whats on the flash disc,i can see the drivers,but in the instructions above it says copy to home directories.,do i need to extract first ?

---

### Post by kostkon on 2007-08-09
I believe you should just select the files, do a right click and select *copy* and then paste them to you *home* directory.

Then do this command as it says
```
sudo cp ~/rt73-cvs-daily.tar.gz /usr/src
```

etc. etc.

---

### Post by nikef on 2007-08-09
thank you will try that

---

### Post by nikef on 2007-08-09
hi i tried that but keep getting,command not know

---

### Post by kostkon on 2007-08-09
Could you be more specific? Where do you get this error message, what are you trying to do?

---

### Post by nikef on 2007-08-09
yes its in the terminal,that's where the error msg comes from 
i am trying to load the drivers ,because the pc with ubuntu on does not have internet accses for me to dowload directly

---

### Post by kostkon on 2007-08-09
OK, did you follow all the steps of the how-to? At which step did your problem occur?

---

### Post by nikef on 2007-08-09
yes followed all steps.
at the first steps and all the way through

1.   open a terminal
2.   Go to the directory where we'll keep the driver's source code:
Code:  cd /usr/src

then i press enter,then this comes up
no such file or diectory

---

### Post by nikef on 2007-08-09
here is abit more info,as to what i am trying to do 

[http://ubuntuforums.org/showthread.php?t=520501&page=2](http://ubuntuforums.org/showthread.php?t=520501&page=2)

---

### Post by nikef on 2007-08-09
Hmm
i seem to be using windows xp more than ubuntu  :(

---

### Post by MenZa on 2007-08-09
You are being very vague. I can tell you, that the reason it's failing, is because the directory /usr/src doesn't appear to exist... which is very strange indeed (I believe this is where the kernel sources are stored?).

Your home directory is not /usr/src. Your home directory is /home/<yourname> (whatever you chose at the installation). You must first mount the flash disk, then copy the files from it. Instructions on how to mount your disks can be found [here](https://help.ubuntu.com/community/Mount). Once you've done that, change to the directory in which you've mounted the device (using 'cd'), then use 'cp <files> <target>' to copy the files to your home directory.

---

### Post by nikef on 2007-08-09
> **MenZa said:**
> You are being very vague. I can tell you, that the reason it's failing, is because the directory /usr/src doesn't appear to exist... which is very strange indeed (I believe this is where the kernel sources are stored?).

Your home directory is not /usr/src. Your home directory is /home/<yourname> (whatever you chose at the installation). You must first mount the flash disk, then copy the files from it. Instructions on how to mount your disks can be found [here](https://help.ubuntu.com/community/Mount). Once you've done that, change to the directory in which you've mounted the device (using 'cd'), then use 'cp <files> <target>' to copy the files to your home directory.

sorry for being very vague,i am very new to linux
and i do not know where to start,the terminal dont seem to work,or is it i am getting conflicting answers :confused: 
thanks for your help,will look at the link you provided

---

### Post by lisati on 2007-08-09
> **nikef said:**
> sorry for being very vague,i am very new to linux
and i do not know where to start,the terminal dont seem to work,or is it i am getting conflicting answers :confused: 
thanks for your help,will look at the link you provided

Keep on smiling - you'll find your way around soon enough.

---

### Post by ogfizzle on 2007-08-09
From what i understood,try extracting to,lets say , desktop.desktop is in the home directory i.e under /home/ur username/Desktop.

---

### Post by nikef on 2007-08-09
> **lisati said:**
> Keep on smiling - you'll find your way around soon enough.

thank you,will try my best lol

---

### Post by nikef on 2007-08-09
> **ogfizzle said:**
> From what i understood,try extracting to,lets say , desktop.desktop is in the home directory i.e under /home/ur username/Desktop.


hey thanks,will give that a shot :)

---

### Post by mali2297 on 2007-08-09
> **nikef said:**
> yes followed all steps.
at the first steps and all the way through

1.   open a terminal
2.   Go to the directory where we'll keep the driver's source code:
Code:  cd /usr/src

then i press enter,then this comes up
no such file or diectory

Do step 6 first (or the alternative if not online). 
> 
6. Install needed dependencies.
Code:

sudo aptitude install build-essential linux-headers-`uname -r`

If you don't have internet access on the Linux install, refer to the section below.


I think that will create the missing directory if it's not already there.

---

### Post by nikef on 2007-08-09
> **mali2297 said:**
> Do step 6 first (or the alternative if not online). 


I think that will create the missing directory if it's not already there.


Hi and thanks

this is the only step that i have managed to do 

also i have the drivers now and put them in my home folder,but the terminal can not find them :confused:

---

### Post by mali2297 on 2007-08-09
> **nikef said:**
> Hi and thanks

this is the only step that i have managed to do 

also i have the drivers now and put them in my home folder,but the terminal can not find them :confused:

As I understand you, you can't even do
```
cd  /usr/src
```

The only thing this does is moving to the directory /usr/src, but you get an error telling you it doesn't exists, right?

Try it again and copy the line exactly.

I find it strange that you don't have that directory.

---

### Post by nikef on 2007-08-10
> **mali2297 said:**
> As I understand you, you can't even do
```
cd  /usr/src
```

The only thing this does is moving to the directory /usr/src, but you get an error telling you it doesn't exists, right?

Try it again and copy the line exactly.

I find it strange that you don't have that directory.

hi and thanks

i did try again and got the same results,but i now how my wireless working :),so i wont need to use that code,at least i dont think so .

---

