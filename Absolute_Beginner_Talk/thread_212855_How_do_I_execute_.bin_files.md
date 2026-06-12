---
title: "How do I execute .bin files"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-10
I was wonderin if there's a way for me to execute .bin file coz I just dled Jre for linux. 
It gives of the error "Cannot open file" & forces me to choose which character coding will work.
God why do they have to use different forms of extention & different ways to open a file.I don't understand the logic!!!

---

### Post by echo $USER on 2006-07-10
Something like > sudo ./nameoffile.bin or maybe > sudo sh nameoffile.bin

---

### Post by jrattner on 2006-07-10
Only use sudo if it needs to be ran as root

---

### Post by kris2pe on 2006-07-10
its in front of my desktop how to I execute it?  Really totally clueless. 
Again what's the obvious, common sense reasoning 4 this? Did MS patented double click & execute procedures? 
Anyways helP!!!

---

### Post by bensexson on 2006-07-10
try sudo chmod +x <file name>.  It needs to be made executable first.

---

### Post by kris2pe on 2006-07-10
> **bensexson said:**
> try sudo chmod +x <file name>.  It needs to be made executable first.

Wohooo!!! Wait which is which? Why are there so many commands? Did you guys memorize this just to make this OS working "normally"?

---

### Post by mostwanted on 2006-07-10
You can install Java through Synaptic, no need to install it using the bin file.

---

### Post by kris2pe on 2006-07-10
Thank you guys!!! 
Thanks also for the link monkey!!!

---

### Post by mscman on 2006-07-10
Ok, first of all, relax. You seem to be making this harder than it is. Yes, many things in Linux require more learning than in Windows, but that's because you STARTED with Windows.

There are "so many commands" because you can't do everything with one command. It's made to be flexible.

Start off by making the file executable:
```
sudo chmod +x /path/to/file
```
Where "/path/to/file" is the path to your .bin file.  For example, if the file was named "file.bin" and was in your /home/USER/Desktop directory, you would run:
```
sudo chmod +x /home/USER/Desktop/file.bin
```
or for a more abbreviated version:
```
sudo chmod +x ~/Desktop/file.bin
```
The "~" is representative of your home directory.

Now we just need to run the executable. To do this, simply type in the full path name of the file; or optionally 'cd' into the directory and use ./file.bin to run it. Using the full path from the previous example, the command would look like:
```
/home/USER/Desktop/file.bin
```
Using the second method, you would add an extra step by doing this:
```
cd /home/USER/Desktop
./file.bin
```

There are some excellent tutorials on using the command line in these forums. One of the best I've found was written by Kyral, and can be found [HERE]("http://www.ubuntuforums.org/showthread.php?t=73885")
Just remember when executing the above commands that the terminal is case sensitive, so when the folder is 'Desktop', don't type in 'desktop', you'll just get an error (or unexpected results if the directory does exist but it's the wrong one...)

---

### Post by barrack on 2006-07-10
MSCMAN: I followed your instructions as I am also curious about running .bin files. (I also looked in Synaptic and what I wanted wasn't there.)

Anyway, it's not a big deal for me, I just want to learn this stuff. I don't really care about the program, but it is the RealPlayer.  

This is what I did...

bc4m@bc4m-PowerBook:/$ sudo chmod +x /home/bc4m/Desktop/RealPlayer10GOLD.bin bc4m@bc4m-PowerBook:/$

As you can see, nothing happened. Thinking that something *may* have happened, I did the next command as you said and I got this.

bc4m@bc4m-PowerBook:/$ /home/bc4m/Desktop/RealPlayer10GOLD.bin
bash: /home/bc4m/Desktop/RealPlayer10GOLD.bin: cannot execute binary file
bc4m@bc4m-PowerBook:/$

Clearly there is a crucial step I'm missing, I just can't figure out what it is. I also have problems installing "regular" tar.gz packages (the ones that aren't available in Synaptic.) I've read what people have said to do, but I am still at a loss.

---

### Post by mscman on 2006-07-10
@Barrack:
Try running the quicktime installer as root and see what happens (add 'sudo' to the beginning of the command to execute it.)  You won't see any response to the chmod command unless there is an error, as is the default for many commands. Another way to install RealPlayer is to use Automatix, which is what I do.

For "installing 'regular' tar.gz packages", you're actually compiling them from source. [Check out this howto for program installation.]("http://doc.gwos.org/index.php/ProgramInstallBeginners") After the information on installing RPM packages, it tells you how to compile from source. If you need help, let me know and I'll send you a PM with instructions.

---

### Post by mostwanted on 2006-07-10
> **kris2pe said:**
> Thank you guys!!! 
Thanks also for the link monkey!!!

lawl no problem.

I'm not a real monkey you know, it's just my alter ego... :P

---

### Post by PingunZ on 2006-07-10
hehe mostwanted, that guide helped me a lot for a .rpm today ;)

:KS :KS :KS !

Grtz PingunZ

---

### Post by kriding on 2006-07-11
I recently installed a .bin file, and the method i used was this:

```
cd Desktop
```which will change your directory to your desktop (assuming that's where your file is, if not, substitute Desktop with the path to your file)

Next make it executable 

```
sudo chmod +x file.bin
```

Finally run the file

```
sudo sh file.bin
```

Remember to replace file.bin with the actual file name

---

### Post by kris2pe on 2006-07-11
Ok thanks I haven't read the blog yet. But I got other recommendation that I should try Easy Ubuntu. You think w/ a name like that you wouldn't have any problems? 
WRONG!!!! That F'ing thing gave a sh+t load of errors!!! 
Here's another question. if the programs is located in like a certain directory would Ubuntu easily locate it just by naming program?
Another question. Why do linux programers need to convert things into exe? instead them converting themselves. Why hassle users w/ that? 
I know I've been comparing it to Windows & I know I shouldn't. But I am so use to Windows I find a steep. Unimaginatively steep curve to climb. 
Here's the error w/ Easy *Hell No* Ubuntu 
[COLOR="Orange"]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors:
--------
dpkg: status database area is locked by another process

EasyUbuntu will not run before these errors are fixed. Please fix them and try again[/COLOR]

Anyone know how to fix this? Easy huh!!!

---

### Post by kriding on 2006-07-11
> **kris2pe said:**
> 
[COLOR="Orange"]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



that would normally mean you have synaptic or some other update process running

---

### Post by MaximB on 2006-07-11
you can run programs located in other directories if you installed them.
just hit "alt+F2" and name your program
and if you mean programs or games that you've copied from the internet without making installations - so it's impossible due to a problem that can happen if you have duplicate names alswere like start.sh in games and start.sh in programs (ubuntu won't know what program or a game you want to run).

---

### Post by barrack on 2006-07-11
> **mscman said:**
> @Barrack:
For "installing 'regular' tar.gz packages", you're actually compiling them from source. [Check out this howto for program installation.]("http://doc.gwos.org/index.php/ProgramInstallBeginners") After the information on installing RPM packages, it tells you how to compile from source. If you need help, let me know and I'll send you a PM with instructions.

This is what happens everytime with the tar.gz thing...

bc4m@bc4m-PowerBook:/$ cd /home/bc4m/Desktop/install_flash_player_7_linux
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$ ./configure
bash: ./configure: No such file or directory
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$ make
bash: make: command not found
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$ sudo make install
Password:
sudo: make: command not found
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$

Ha ha, do i have to install the command?

---

### Post by mscman on 2006-07-11
> **barrack said:**
> This is what happens everytime with the tar.gz thing...

bc4m@bc4m-PowerBook:/$ cd /home/bc4m/Desktop/install_flash_player_7_linux
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$ ./configure
bash: ./configure: No such file or directory
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$ make
bash: make: command not found
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$ sudo make install
Password:
sudo: make: command not found
bc4m@bc4m-PowerBook:~/Desktop/install_flash_player_7_linux$

Ha ha, do i have to install the command?

Did you install the package build-essential? If not, you should do so.  That's why your make command is failing: make is not installed.

---

### Post by avtolle on 2006-07-11
OK, it looks like the OP may be on a Mac; please let us know what your system is. If you are trying to install Flash, be aware there are issues with PPC Linux and Flash.

---

### Post by barrack on 2006-07-11
> **avtolle said:**
> OK, it looks like the OP may be on a Mac; please let us know what your system is. If you are trying to install Flash, be aware there are issues with PPC Linux and Flash.

Ah, you're right. I'm on a mac. I wasn't aware of the issue. Still, I am not able to install other tar.gz files. The flash one was just an example.

It was just suggested that I install build-essential. I'm not sure where or what I need to do to install that. Any help?

---

### Post by avtolle on 2006-07-11
Yes, you should install build-essential. You should do it, IMHO,through Synaptic (System -->Administration-->Synaptic Package Manager). Do a search for "build-essential", mark it for installation (if it is not already installed), then select "Apply". BTW, do you have the extra repositories enabled? I cannot remember if you need to do this for build-essential, but it is a good idea to enable them in any event.

---

### Post by barrack on 2006-07-11
> **mscman said:**
> Did you install the package build-essential? If not, you should do so.  That's why your make command is failing: make is not installed.

This did the trick. It was a crucial step that, for some reason, only you could see. Ha ha. Thanks so much!

---

### Post by barrack on 2006-07-11
> **kriding said:**
> I recently installed a .bin file, and the method i used was this:

```
cd Desktop
```which will change your directory to your desktop (assuming that's where your file is, if not, substitute Desktop with the path to your file)

Next make it executable 

```
sudo chmod +x file.bin
```

Finally run the file

```
sudo sh file.bin
```

Remember to replace file.bin with the actual file name

I cannot thank you all enough for the assistance. I just wanna say that. I am able now to install tar.gz (except of course for the flash player that doesn't work on the ppc, which i just learned!) Now i am attempting to work on .bin installations. I have followed both what Real says and what is quoted above. Below is what I'm getting. Is there a similar missing step that I don't know about as when I was working with tar.gz (ie, instaling something like build-essential)

bc4m@bc4m-PowerBook:~/Desktop$ sudo chmod +x RealPlayer10GOLD.bin
bc4m@bc4m-PowerBook:~/Desktop$ sudo sh RealPlayer10GOLD.bin
RealPlayer10GOLD.bin: RealPlayer10GOLD.bin: cannot execute binary file
bc4m@bc4m-PowerBook:~/Desktop$

---

### Post by oczindian03 on 2006-07-11
I am also trying to get realplayer. I did the same thing... I typed in 
sudo chmod a+x RealPlayer10GOLD.bin

but then to my surprise it asked for a password? Is that my login password? I tried my login password but it didn't work. HELP!:confused: :confused:

---

### Post by Ragazzo on 2006-07-11
> **barrack said:**
> I cannot thank you all enough for the assistance. I just wanna say that. I am able now to install tar.gz (except of course for the flash player that doesn't work on the ppc, which i just learned!) Now i am attempting to work on .bin installations. I have followed both what Real says and what is quoted above. Below is what I'm getting. Is there a similar missing step that I don't know about as when I was working with tar.gz (ie, instaling something like build-essential)

bc4m@bc4m-PowerBook:~/Desktop$ sudo chmod +x RealPlayer10GOLD.bin
bc4m@bc4m-PowerBook:~/Desktop$ sudo sh RealPlayer10GOLD.bin
RealPlayer10GOLD.bin: RealPlayer10GOLD.bin: cannot execute binary file
bc4m@bc4m-PowerBook:~/Desktop$

Try: sudo ./RealPlayer10GOLD.bin

If it doesn't work, what does "file RealPlayer10GOLD.bin" print?

---

### Post by oczindian03 on 2006-07-11
> **Ragazzo said:**
> Try: sudo ./RealPlayer10GOLD.bin
**^^^ That one came back with the password prompt**
If it doesn't work, what does "file RealPlayer10GOLD.bin" print?
**^^^ That one said error can't find it**

---

### Post by avtolle on 2006-07-11
Please check the RealPlayer binary you dl'ed and assure yourself it is for PPC; I think (but do not recall) the binary you have there is for i386. Hope I'm wrong...:-k

---

### Post by Ragazzo on 2006-07-11
> **oczindian03 said:**
> I am also trying to get realplayer. I did the same thing... I typed in 
sudo chmod a+x RealPlayer10GOLD.bin

but then to my surprise it asked for a password? Is that my login password? I tried my login password but it didn't work. HELP!:confused: :confused:

Yes, it's your login password. When you wrote the password, did it say "Sorry, try again." and prompted for the password again?

---

### Post by oczindian03 on 2006-07-11
Yea it said sorry try again. Then eventually it said 3 wrong tries or something.

---

### Post by kris2pe on 2006-07-11
God it got worst!
I redo the entire think & guess what it hangs up!!!
after asking me my password & hangs up. Doesn't do a thing!!! Doesn't give errors nothing!!!

---

### Post by avtolle on 2006-07-11
Sorry to hear that. The purpose of my earlier post concerning the appropriate version of the binary was occasioned by the notation at real.com under the archived file section of the "experimental" (I think this is right) nature of an installer for ppc linux. The existence of the same led me to think that the binary you are attempting to install might not be configured for ppc. With that said, I have the following two options for your consideration:

1) Download the experimental installer, and then see if it will run; or

2) Register, and download the source file (realplay-10.0.5-source.tar.bz2,located under Archived Releases - Helix Community, which is where you likely found the binary with which you are struggling), which you would then compile.

I haven't the time right now to explore either of these options, but merely set them out for your consideration. Best of luck.

---

### Post by kris2pe on 2006-07-13
I was able fix it by reformating & reinstalling the whole thing!!!

---

