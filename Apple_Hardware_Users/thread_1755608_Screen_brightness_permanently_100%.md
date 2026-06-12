---
title: "Screen brightness permanently 100%"
date: 2011-05-11
forum: Apple Hardware Users
---

### Post by wbchilds on 2011-05-11
Hey, I'm new to Linux. Everything has been great so far and I love Ubuntu.

I originally installed Maverick on my Macbook 5.1 using rEFIt to dual boot. For some reason, after installing Compiz my screen brightness functionality stopped working. It was permanently 100%. Searching forums, I found that it's a fairly common problem. Unfortunately, none of the solutions there helped. I thought that upgrading to Natty might work, but no luck. So far I've tried changing the brightness manually in terminal and in power-management,  editing the grub file  and also reinstalling compiz, all to no avail.

Trying to alter brightness using the fn keys displays the brightness panel in the top right, and it decreases in value as it should, but the screen stays bright. The brightness settings work fine when I boot to Mac.

Any help would be much appreciated by both my battery and my eyes.

---

### Post by Lars Noodén on 2011-05-11
I have the same issues with a Macbook Pro 8.3. The brightness buttons have no effect on the actual screen brightness though they affect the brightness meter.

---

### Post by handy on 2011-05-11
Controlling the screen brightness:

Below is the C code for a little program that adjusts the brightness on many LCD Apple screens (I have been using it now for over 3 years +). It is easy to compile & setup using the following instructions.


The instructions follow:

Copy & paste the C code (found below these instructions) to your /home. Save the code as a file, backlight.c

Now open a terminal in the directory where backlight.c is located.

Type the following in the Terminal:

gcc -o backlight backlight.c

You now have a program called backlight. It should adjust the brightness.

To change the brightness, you have to have direct access to video memory, which means that you have to be superuser (root).

Type su, then your root password when prompted.

Now test the program by typing ./backlight 10 in the terminal.

You can give it values from 1 to 15. Find a value you like.

Now enter the following in the Terminal:

cp backlight /usr/local/bin.

Which copies the program to the standard location for user installed programs.

Next, (**in Arch**) to run it at startup;- still as root, edit /etc/rc.local, add a line saying /usr/local/bin/backlight N, where N is the number code you want for the brightness. 

*** For Ubuntu, you do the same as above, but you will have to fish out the Ubuntu way (meaning the file you add the command line to) of running this little program at startup. It is not hard to do (I just don't remember how to do it anymore. :)) ***

The tiny amount of source code follows:

```

/*
* Apple Macbook Pro LCD backlight control
*
* Copyright (C) 2006 Nicolas Boichat <nicolas @boichat.ch>
* Copyright (C) 2006 Felipe Alfaro Solana <felipe_alfaro @linuxmail.org>
*
* This program is free software; you can redistribute it and/or modify
* it under the terms of the GNU General Public License as published by
* the Free Software Foundation; either version 2 of the License, or
* (at your option) any later version.
*
* This program is distributed in the hope that it will be useful,
* but WITHOUT ANY WARRANTY; without even the implied warranty of
* MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
* GNU General Public License for more details.
*
* You should have received a copy of the GNU General Public License
* along with this program; if not, write to the Free Software
* Foundation, Inc., 675 Mass Ave, Cambridge, MA 02139, USA.
*
*/

#include <stdio.h>
#include <sys/io.h>
#include <stdlib.h>

void init()
{
    if (ioperm(0xB2, 0xB3, 1) < 0)
    {
        perror("ioperm failed (you should be root).");
        exit(2);
    }
}

int get_current_value()
{
    outb(0x03, 0xB3);
    outb(0xBF, 0xB2);
    char t = inb(0xB3) >> 4;
    return t;
}

int calculate_new_value(const char *arg)
{
    int val, new = atoi(arg);

    if (arg[0] == '+' || arg[0] == '-')
        val = new + get_current_value();
    else
        val = new;

    if (val > 15)
        val = 15;
    else if (val < 1)
        val = 1;

    return val;
}

int main(int argc, char** argv)
{
    if (argc > 2)
    {
        printf("Usage:\n");
        printf("%s : read current value\n", argv[0]);
        printf("%s value : write value [0-15]\n", argv[0]);
        exit(1);
    }

    init();

    if (argc < 2)
    {
        printf("Current value : %d\n", get_current_value());
        exit(0);
    }

    if (argc == 2)
    {
        int value = calculate_new_value(argv[1]);
        outb(0x04 | (value << 4), 0xB3);
        outb(0xBF, 0xB2);
        printf("new value: %d\n", value);
    }

    return 0;
}

```

By the way, I've been using this code on a 2007 model 24" iMac.

---

### Post by wbchilds on 2011-05-11
I tried running the code as you said, it appears to be working (i.e. it prints "new value = 5" etc) but still the brightness doesn't change.

---

### Post by handy on 2011-05-12
> **wbchilds said:**
> I tried running the code as you said, it appears to be working (i.e. it prints "new value = 5" etc) but still the brightness doesn't change.

Have you tried inputting extreme values within the software's range, to see if they have an effect?

---

### Post by wbchilds on 2011-05-12
Yep, I tried that too. No matter how high my input it always just prints 'new value: 15'. If I input 0 it returns 1 and negative numbers give the results backwards (i.e -1 is 14, -2 is 13 etc). There's no change to the screen brightness itself with any of these inputs, however.

---

### Post by handy on 2011-05-13
That software is obviously not compatible with your monitor/computer unfortunately.

There is another piece of software that people are using. I can't remember its name, but it is talked about in this sub-forum.

---

### Post by wbchilds on 2011-05-13
Found a fix! I don't know how I missed it before.

Basically I just installed 'nvclock' and now I can set brightness in terminal. Thanks for your help!

---

### Post by handy on 2011-05-13
> **wbchilds said:**
> Found a fix! I don't know how I missed it before.

Basically I just installed 'nvclock' and now I can set brightness in terminal. Thanks for your help!

That's great that you have got it sorted. :)

Could you mark the thread as [SOLVED] ?

---

### Post by samuaz on 2011-05-13
Install pommed.... sudo apt-get install pommed

---

### Post by wbchilds on 2011-05-13
Yeh, I tried that earlier on, but had no luck. Don't know what nvclock is doing, but it's doing something right. Maybe it's just accessing my video card in a more direct manner?

I would like to know exactly what is wrong and maybe get a better fix. It's a bit annoying not being able to use the fn buttons to change brightness and the lower brightness limit really isn't that low. Or not as low as it goes under mac osx anyhow.

---

### Post by maito78 on 2011-05-22
Hi everyone
 I have recently entered in ubuntu world and I have a macbook 5,1. I have had the same problem that you mentioned and I could fix it by adding  
 
 Section "Device"
    Identifier "Default Device"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
 
 in xorg.conf (in /etc/x11).   
 Now using F1 and F2 I can adjust the brightness.
 I found this fix at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/743352](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/743352) in post 7.

---

### Post by wbchilds on 2011-05-23
This worked. Many thanks!

---

