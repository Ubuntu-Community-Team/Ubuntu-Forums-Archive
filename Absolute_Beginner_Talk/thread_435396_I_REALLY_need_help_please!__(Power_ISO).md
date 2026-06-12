---
title: "I REALLY need help please!  (Power ISO)"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by princeofhosts on 2007-05-06
Hi, I need to burn a .daa file and I have DLed the PowerISO.tar.gz

what do i do with it?

I run the "cd poweriso make" command and it does not work

i am new to linux so please help me as easy as possible

thanks!

---

### Post by pay on 2007-05-06
install the needed compilers ```
sudo aptitude install build-essential
```extract it```
tar zxvf PowerIso.tar.gz
```Change into the directory```
cd PowerIso*
```configure it```
./configure
```compile it```
make
```install it```
sudo make install
```

---

### Post by starcraft.man on 2007-05-06
[Here]("http://www.cyberciti.biz/faq/how-do-i-open-daa-direct-access-archive-files-under-linux-or-unix-oses/") you go, a good link to help :)

---

### Post by princeofhosts on 2007-05-06
> **pay said:**
> install the needed compilers ```
sudo aptitude install build-essential
```extract it```
tar zxvf PowerIso.tar.gz
```Change into the directory```
cd PowerIso*
```configure it```
./configure
```compile it```
make
```install it```
sudo make install
```

I'm sorry I get lost at the second step...could you explain that?

And when I drag the extracted file to my terminal, it says that no such directory is there.

I'm so lost...

-sigh-

---

### Post by Nythain on 2007-05-06
just downloaded linux binary from the website... doesnt even need to be made or installed... just ./poweriso whateveryouneed to do

---

### Post by pay on 2007-05-06
Sorry. My fault. I thought it was source code. Try opening the terminal and typing ```
wget http://www.poweriso.com/poweriso-1.1.tar.gz
tar zxvf poweriso
./poweriso
```and if you want it to work everytime you type poweriso in then```
sudo cp poweriso /usr/bin
```

---

### Post by princeofhosts on 2007-05-06
> **Nythain said:**
> just downloaded linux binary from the website... doesnt even need to be made or installed... just ./poweriso whateveryouneed to do

I don't understand how to do this...
...I just need to burn a .daa to a DVD.

What's the best way to do this?

Can I get step-by-step instructions as well?

I am 100% new to Ubuntu.

---

### Post by princeofhosts on 2007-05-06
None of this, worked for me...
...does anyone have any idea?

Please?

---

### Post by Nythain on 2007-05-06
i dont think poweriso is your solution for burning a .daa directly... it can however convert the .daa to .iso...
```

rune@lutz:~/Desktop$ ls
poweriso
rune@lutz:~/Desktop$ ./poweriso -?

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

Usage:    poweriso <command> [parameters] [-switches]

<Commands>

 list <image file> <directory>    List files and directories in image file.
     Example:  List all files and directories in root direcory of /home/sam/test.iso .
     Command:  poweriso list /home/sam/test.iso / -r

 extract <image file> <dir/file name>   Extract files/directories from image file.
     Example:  Extract all files and directories in root direcory of /home/sam/test.iso
               to /home/sam/test recursively.
     Command:  poweriso extract /home/sam/test.iso / -od /home/sam/test

 convert <image file>    Convert image file to other format.
     Example:  Convert /home/sam/test.daa to standard iso file
     Command:  poweriso convert /home/sam/test.daa -o /home/sam/test.iso -ot iso

<Switches>

 -r             List or extract recursively.
 -o             Specify output image file name.
 -od            Specify output folder.
 -ot <iso|daa|bin>    Specify output image file type. If not specified,
                the image type will be determined by file name suffix.
 -volsize <n>   Split output image file to multiple volumes, and set volume
                size to <n>. Example: -volsize 100M
 -setpassword <password>   Set password for output image file.
                Example: -setpassword 12345678
rune@lutz:~/Desktop$ 

```there are also other programs that can do such things also, like acetoneiso

just stumbled upon this other thread [http://ubuntuforums.org/showthread.php?t=189016](http://ubuntuforums.org/showthread.php?t=189016) so you might be a little out of luck on just straight burning the .daa file wihout converting it to a better formate (like .iso) first

---

### Post by princeofhosts on 2007-05-06
> **Nythain said:**
> i dont think poweriso is your solution for burning a .daa directly... it can however convert the .daa to .iso...
```

rune@lutz:~/Desktop$ ls
poweriso
rune@lutz:~/Desktop$ ./poweriso -?

PowerISO   Copyright(C) 2004-2006 PowerISO Computing, Inc
            Type poweriso -? for help

Usage:    poweriso <command> [parameters] [-switches]

<Commands>

 list <image file> <directory>    List files and directories in image file.
     Example:  List all files and directories in root direcory of /home/sam/test.iso .
     Command:  poweriso list /home/sam/test.iso / -r

 extract <image file> <dir/file name>   Extract files/directories from image file.
     Example:  Extract all files and directories in root direcory of /home/sam/test.iso
               to /home/sam/test recursively.
     Command:  poweriso extract /home/sam/test.iso / -od /home/sam/test

 convert <image file>    Convert image file to other format.
     Example:  Convert /home/sam/test.daa to standard iso file
     Command:  poweriso convert /home/sam/test.daa -o /home/sam/test.iso -ot iso

<Switches>

 -r             List or extract recursively.
 -o             Specify output image file name.
 -od            Specify output folder.
 -ot <iso|daa|bin>    Specify output image file type. If not specified,
                the image type will be determined by file name suffix.
 -volsize <n>   Split output image file to multiple volumes, and set volume
                size to <n>. Example: -volsize 100M
 -setpassword <password>   Set password for output image file.
                Example: -setpassword 12345678
rune@lutz:~/Desktop$ 

```
there are also other programs that can do such things also, like acetoneiso

I have Acetoneiso but every time I try to click a button, nothing works...

---

### Post by pay on 2007-05-07
```
poweriso convert in_file.daa -o out_file.iso -ot iso
```

---

### Post by Josh1 on 2007-05-07
Pay, that is the same method that I use, then I burn the cd directly from the .iso :).

---

### Post by Kaobear on 2007-05-21
> **pay said:**
> ```
poweriso convert in_file.daa -o out_file.iso -ot iso
```



Worked absolutely perfectly.

Now, if only people would stop using proprietary software.....

---

### Post by acfs4 on 2008-01-22
Hey i did everything suggested in this forum once and the last one:

poweriso convert in_file.daa -o out_file.iso -ot iso 

seems like the best one but i keep getting a Bash: poweriso: Command not found

any suggestions?

---

### Post by emarkd on 2008-01-22
You don't have the software yet.

```
$ wget http://poweriso.com/poweriso.tar.gz
$ tar -zxvf poweriso.tar.gz
```

---

### Post by bulletxt on 2008-01-23
Just download latest AcetoneISO2 2.0 RC1 ubuntu package from official site. It will do everthing for you.
the package is for ubuntu gutsy 7.10. if you are on feisty then you must upgrade the qt4 packages from synaptic enabling the feisty-backports rep allways from synaptic.

If you are on a 64-bit OS then download the source and compile it. it's very easy and it's written in the readme inside how to do it.

---

### Post by acfs4 on 2008-01-23
I had downloaded it the (what i am forced to call ) windows way and extracted it and then i tried the:


Code:

$ wget [http://poweriso.com/poweriso.tar.gz](http://poweriso.com/poweriso.tar.gz)
$ tar -zxvf poweriso.tar.gz

that just re-downloads it but poweriso sill refuses to be used as a command:

Bash: poweriso: command not found

Thanks for any suggestions

---

### Post by brander on 2008-01-23
This is like almost everything for Linux, it just does not work. For example I have followed the previous instructions and typed

./poweriso

which gives me the hint:

type poweriso -? for a list of commands. So I try typing that and I get the an error message. Goes like this:

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

nickc@Asrock01:~/Temp/PowerIso$ poweriso -?
bash: poweriso -?: command not found

Hopeless.

---

### Post by acfs4 on 2008-01-23
> **brander said:**
> This is like almost everything for Linux, it just does not work. For example I have followed the previous instructions and typed

./poweriso

which gives me the hint:

type poweriso -? for a list of commands. So I try typing that and I get the an error message. Goes like this:

PowerISO   Copyright(C) 2004-2007 PowerISO Computing, Inc
            Type poweriso -? for help

nickc@Asrock01:~/Temp/PowerIso$ poweriso -?
bash: poweriso -?: command not found

Hopeless.

i think i can help with that one it worked for me if i mixed the two that is if I

Code:

XXXX: ~$  ./poweriso -?

i finally got it to work the full command seems to be:[I]

XXXX: ~$  ./poweriso convert in_file.daa -o out_file.iso -ot iso[/I]

at least this is for conversions from daa to iso

---

