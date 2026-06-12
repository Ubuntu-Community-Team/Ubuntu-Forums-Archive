---
title: "[SOLVED] Permanent startup code"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by kbless7 on 2008-01-19
I have this problem in Matlab 2007a in which I have to run the following code to change the java in  matlab.

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
```

The problem is when I exit the terminal it just acts like it never happened and defaults to matlabs original java which doesn't work. So is there some way to permanently run this code upon startup?

Second, when I run the command for matlab, the program doesn't stay open unless I do it from the terminal. Any ideas on that one?

Thanks in advance.

-Matt

---

### Post by smartboyathome on 2008-01-19
Try saving this code as a file named .matlab.sh in your home folder:
```
#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
```
And then add it to your startup (System > Preferences > Sessions).

---

### Post by kbless7 on 2008-01-19
Thanks for the quick reply, but that doesn't work. It still only uses the right java when i run it through the terminal. Any one else?

---

### Post by nhandler on 2008-01-19
Try adding the line to ~/.bashrc.

---

### Post by kbless7 on 2008-01-19
> **Cheater said:**
> Try adding the line to ~/.bashrc.

That absolutely worked. Thanks a bunch Cheater.

Onto the next problem. The command to run matlab is just
```
.matlab/bin/matlab
```

it only stays running if I type that in the terminal, but it doesn't with a launcher or alt-f2. Any ideas on how to get a launcher to work.

-Matt

---

### Post by nhandler on 2008-01-23
You can try setting this as the command for the launcher

```
/home/YOURUSERNAME/.matlab/bin/matlab
```
You only were using the relative path. The command I have above includes the absolute path to the executable. That should make the launcher and alt+f2 work. Another option is to type this command
```
sudo ln -s /home/YOURUSERNAME/.matlab/bin/matlab /usr/bin/matlab
```
After doing that command, you should be able to simply type
```
matlab
```
In a terminal/launcher/alt+f2 to launch the program.

---

### Post by Whiffle on 2008-01-23
Do this:


Make a file, name it whatever you want, put this in it:
```

#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
~/.matlab/bin/matlab -desktop

```

chmod +x it, and make a launcher for it, i think it should work.  It might need another - on the -desktop part, i can't remember.  Shouldn't need to run it in a terminal.

---

### Post by kbless7 on 2008-01-23
> **Whiffle said:**
> Do this:


Make a file, name it whatever you want, put this in it:
```

#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre
~/.matlab/bin/matlab -desktop

```

chmod +x it, and make a launcher for it, i think it should work.  It might need another - on the -desktop part, i can't remember.  Shouldn't need to run it in a terminal.

Yep. I actually figured that out 2 days ago. Thanks.

---

