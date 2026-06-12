---
title: "Really easy Flash question:"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by aberadam on 2007-06-03
> In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

How do I navigate to the directory?

---

### Post by nitro_n2o on 2007-06-03
```
tar -xzvf install_flash_player_9_linux.tar.gz
cd install_flash_player_9_linux
```

now you r in the directory

---

### Post by aberadam on 2007-06-03
Thanks.

---

### Post by aberadam on 2007-06-03
I just tried what you said and got this: 

> adam@adam-desktop:~$ tar -xzvf install_flash_player_9_linux.tar.gz
tar: install_flash_player_9_linux.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
adam@adam-desktop:~$ cd install_flash_player_9_linux
bash: cd: install_flash_player_9_linux: No such file or directory
adam@adam-desktop:~$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
adam@adam-desktop:~$ 


---

### Post by aberadam on 2007-06-03
YouTube doesn't work.

---

### Post by diatribe on 2007-06-03
you need to be in the directory you downloaded the file to, probably ~/Desktop

---

### Post by Ek0nomik on 2007-06-03
What **diatribe** said is correct.  You need to make sure when you execute the command, it knows where the file is.

If you saved it to your desktop, you can get there via terminal by typing:

```
cd /home/**yourusername**/Desktop
*or*
cd ~/Desktop

```

Then run the command diatribe mentioned.  :)

---

### Post by aberadam on 2007-06-03
Thanks a lot, but I still can't get it to work: 

> bash: cd: /home/yourusername/Desktop: No such file or directory
adam@adam-desktop:~$ cd /home/adam/Desktop
adam@adam-desktop:~/Desktop$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
adam@adam-desktop:~/Desktop$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
adam@adam-desktop:~/Desktop$ cd ~/Desktop
adam@adam-desktop:~/Desktop$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory
adam@adam-desktop:~/Desktop$ 


---

### Post by Outrunner on 2007-06-03
type ```
cd
```

then post the output of ```
ls
```

and ```
cd Desktop/
ls
```

---

### Post by aberadam on 2007-06-03
Thanks guys. 

I got it working by right clicking and 'extract' and then 'run in terminal'.  

YouTube works!

---

