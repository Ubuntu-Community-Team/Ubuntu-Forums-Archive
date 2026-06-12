---
title: "need help removing &quot;/usr/share/games/SecondLife_i686_1_18_1_2&quot; folder"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by cmlewin on 2007-08-15
hey, thanks for the quick help...

i tried to download/install secondlife using the package on getdeb.net, but the install didn't work... and i sorta don't really care and just want to remove the "/usr/share/games/SecondLife_i686_1_18_1_2" folder now... however when i locate it and hit the delete key i get the message: "Cannot move "/usr/share/...6_1_18_1_2" to the trash because you do not have permissions to change it or its parent folder." I assume this means I should do it in terminal as root, however I've only been on Ubuntu (Feisty) for a couple days and have no idea how... Please help!

Thanks again.

---

### Post by jnorthr on 2007-08-15
look for the picture of a terminal, or from the menu bar there is a drop down showing 'terminal' - sorry can't remember which one.

Once terminal is started, enter:
sudo rm xxx
you'll be asked for your superuser password

---

### Post by jnorthr on 2007-08-15
whoa - my mistake it's not 'rm' to remove a directory but i can't think of another command to do it. rmdir ? from a terminal command line you can do 'man rm' to look at the manual documentation for that command. in there it should tell you how to blitz directories. Welcome aboard !! :)

---

### Post by Acksys on 2007-08-15
First of all, how did you install the package? You might want to try

```
dpkg -r packagename.deb
```

Type this in the directory in which the .deb file is located. If the folder is still present after that, you can delete the folder with this command:

```
sudo rm -rf /usr/share/games/SecondLife_i686_1_18_1_2
```

At the prompt, type the password of your main account.
In the terminal, type "man sudo" (no quotes) or "man dpkg" (no quotes) for more information about these commands and their switches.

---

### Post by bodhi.zazen on 2007-08-15
If you prefer a gui, open a terminal and type :

```
gksu nautilus /usr/share/games/
```

You can then delete at will

Careful with that though, you are running nautilus as root.

---

### Post by cmlewin on 2007-08-15
thanks everyone, i just did the gui one that  bodhi gave me, but the terminal one was really what i was looking for... i'm definitely going to come back to this forum though as that was an amazingly quick response

much love.

---

### Post by st33med on 2007-08-15
Also, you dl'd the wrong thing. You're supposed to download an i386 version...

Of course, it depends on your processor. If you're using 64-bit Ubuntu, dl the AMD64 version.

---

### Post by speaker219 on 2007-08-15
you could also run a command like

```
sudo rm -Rdf /usr/share/games/SecondLife_i686_1_18_1_2
```

That would remove the folder and all of its contents

---

### Post by cmlewin on 2007-08-15
okay another problem occurred now... i deleted the folder using the nautilus as root GUI as i mentioned before... howevvver.. now when i do "sudo apt-get upgrade"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

i tried to place the folder back where it was using the same nautilus as root GUI but i get the same error... what now? thanks!

---

### Post by R0B071CxN1NJ4 on 2007-08-15
First: Go the parent file like this:

```
# cd /usr/share/games
```Then: Remove the file with:

```
# sudo rm -r SecondLife_i686_1_18_1_2
```Finally: Remove all excess files left over with:

```
# sudo apt-get autoremove
```You should be rid of the unwanted file

note: anytime you want to find out why a command isnt working type --help after the base command.

---

### Post by cmlewin on 2007-08-15
> **R0B071CxN1NJ4 said:**
> First: Go the parent file like this:

```
# cd /usr/share/games
```Then: Remove the file with:

```
# sudo rm -r SecondLife_i686_1_18_1_2
```Finally: Remove all excess files left over with:

```
# sudo apt-get autoremove
```You should be rid of the unwanted file

note: anytime you want to find out why a command isnt working type --help after the base command.

thanks but i still get the same error:

cameron@cameron-laptop:/$ su
Password: 
root@cameron-laptop:/# cd /usr/share/games
root@cameron-laptop:/usr/share/games# rm -r SecondLife_i686_1_18_1_2
rm: cannot remove `SecondLife_i686_1_18_1_2': No such file or directory
root@cameron-laptop:/usr/share/games# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.

---

### Post by Nervouswreck on 2007-08-15
I would suggest making sure you don't have anything else you want to keep, blitzing the path, and starting over
```

sudo rm -r pathname

```
And redownload.

---

### Post by cmlewin on 2007-08-15
blitzing?

---

### Post by cmlewin on 2007-08-15
now i tried to re-download the .deb package from getdeb, but to no avail...it now gives me an error of corruption... and i cannot even enter the synaptic package manager... HELP ME PLEASE! i'm so close to punching a hole thorugh the computer... why linux whyyyyyyyyyy

---

### Post by bodhi.zazen on 2007-08-15
re download the exact .deb

re install it

then remove it via any tool you like.

---

### Post by cmlewin on 2007-08-15
> **bodhi.zazen said:**
> re download the exact .deb

re install it

then remove it via any tool you like.

i tried to do that from getdeb.net

but when it automatically opens in the deb installer i get this message:

Could not open 'secondlife-install-1.18.1.2-1~getdeb1_i386.deb'
The package might be corrupted or you are not allowed to open the file.  Check the permissions of the file.

Now what?
Argh argh Damn.

Thanks for the continual assistance though....

---

### Post by cmlewin on 2007-08-15
bueler?

just to let people know i think this MAY have solved my problem... seems to have so far, but we'll see

[http://ubuntuforums.org/showthread.php?p=3158679](http://ubuntuforums.org/showthread.php?p=3158679)

thanks to everyone...

---

