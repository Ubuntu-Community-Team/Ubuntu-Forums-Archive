---
title: "bash: Permission denied"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by vpik01 on 2008-02-18
Hi everyone, first post in my first attempt at linux... I'm using an IBM/lenovo X41 Tablet PC with Ubuntu 7.10 and have had a good experience so far.  

My first tough spot has been trying to get the swivel screen and stylus for the tablet functionality to work.  I have been following an excellent  wiki;

[HTML]http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_on_a_ThinkPad_X41_Tablet[/HTML]

I got through the thumb scroll and the stylus (I think... can't verify till the ACPI Swivel is fixed) and have gotten stuck at the ACPI Swivel. So far I created the x41tsdown.sh and x41tsup.sh files.

The next instruction:```

sudo chown root.root /etc/acpi/x41tsdown.sh
sudo chmod 755 /etc/acpi/x41tsdown.sh
sudo chown root.root /etc/acpi/x41tsup.sh
sudo chmod 755 /etc/acpi/x41tsup.sh
```
Is where I am at now.  I have typed these in the terminal and nothing seems to happen, I tried several times with different chmod ### (660, 666 and 644) and still nothing.

I then went ahead with the following code as directed in the wiki:
```
sudo cat <<EOF > /etc/acpi/events/x41t-swivel-down
# /etc/acpi/events/x41t-swivel-down
# called when tablet head swivels down
event=ibm/hotkey HKEY 00000080 00005009
action=/etc/acpi/x41tsdown.sh
EOF
```
And I get the error:```

bash: /etc/acpi/events/x41t-swivel-down: Permission denied
```
I've been running google searches, and looking within the forum - i'm sure this has been answered but I obviously don't know enough to recognize the answer... any help would be most welcome!

Thanks!

---

### Post by spiderbatdad on 2008-02-18
try ```
sudo chmod a+x x41t*.sh
```

---

### Post by vpik01 on 2008-02-18
spiderbatdad - thanks for the quick post... unfortunately ```
sudo chmod a+x x41t*.sh 
``` didn't work.  This is what I see:
```
tony@4310:~$ sudo chmod a+x /etc/acpi/x41tsdown.sh
tony@4310:~$ sudo cat <<EOF > /etc/acpi/events/x41t-swivel-down
> # /etc/acpi/events/x41t-swivel-down
> # called when tablet head swivels down
> event=ibm/hotkey HKEY 00000080 00005009
> action=/etc/acpi/x41tsdown.sh
> EOF
bash: /etc/acpi/events/x41t-swivel-down: Permission denied
tony@4310:~$
```
 
I tried it twice, the first time I used the line you suggested terminal did ask me for my pwd which I put in, the second time I guess I was within the time limit so there was no request... did I use your code wrong? Thanks!

---

### Post by spiderbatdad on 2008-02-18
from my limited experience, it looks as though the script x41t-swivel-down is not executable. I don't know where you have put these scripts, nor why they are owned by root instead of user.  At any rate, there is a permissions issue with one or all of you x41t...sh scripts. 755 on each of them should produce the desired result.

could you post an ls -l of those scripts?

---

### Post by spiderbatdad on 2008-02-18
I see now...it looks as though you are logged in as a user that may be other than Admin. Check your user privileges under Users and Groups>>User Privileges tab.

---

### Post by vpik01 on 2008-02-18
There are two accounts; tony and root.

My account (tony) seems to have the appropriate permissions checked; the only ones NOT checked are 
- Allow use of fuse filesystems like LTSP Thin Client blockdevice
- Send and receive faxes
- Use tape drives

The ls -l for x41tsdown.sh is:```

-rwxr-xr-x l root root 462 2008-02-18 18:46 /etc/acpi/x41tsdown.sh
```

Does that shed any further light?

---

### Post by spiderbatdad on 2008-02-18
yes that looks good. the same permissions should be set for x41tsup.sh and x41t-swivel-down.sh

---

### Post by bodhi.zazen on 2008-02-18
The problem is you can not redirect with sudo that way, ie you can not pipe or > directly

So you can become root :

```
sudo -i
```

And run those commands without sudo in front 

OR use sudo like this :

```
sudo sh "cat <<EOF > /etc/acpi/events/x41t-swivel-down
> # /etc/acpi/events/x41t-swivel-down
> # called when tablet head swivels down
> event=ibm/hotkey HKEY 00000080 00005009
> action=/etc/acpi/x41tsdown.sh
> EOF"
```

:twisted:

---

### Post by vpik01 on 2008-02-18
bodhi.zazen -

Thanks!  so with 'sudo -i' I was finally able to run the code... :) now as it turns out I haven't achieved the goal of being able to go to tablet mode. Neither the stylus or the acpi swivel is recognizing going to tablet 'mode'...

I will have to do some more research on this and try again.  Thank you again for the help.  I've read that taking the root profile can be dangerous, is it preferable (especially for a new user) to use the 'sudo sh' command rather than the 'sudo -i'?

I'll post an update when I try again on this... or when I hit another wall!

---

### Post by bodhi.zazen on 2008-02-18
sudo -i is fine, as with sudo, just be careful what you do and log out when done. I use sudo -i when I have to do sys admin rather then typing sudo over and over.

If it is just a fwe (or single) command, sudo is fine.

"Running as root" generally refers to logging in as root, or running X as root, which can be done but is a security risk and is not needed.

---

