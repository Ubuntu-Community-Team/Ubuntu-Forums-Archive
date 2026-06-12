---
title: "Desktop OWNERship"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-06
I think I should change my name to UbuntuSOD. I envy the folks that have a "trouble free" installation. I'm at the point of forgetting Linux existed.  The thing is the bits that's working make it worthwhile, so I want it all.

I have one major issue that keeps biting me back, even though I manage to work around the issues. In the desktop, I am not able to become the root user or file owner and it is a real PIA.

The package manager don't open. I cannot add or edit users. I cannot save or edit files etc etc. The "normal user" things work fine, but as soon as I tried to copy files or install or extract, I get the "no permission" bit. The only way is to use the CLI or run as different user options. The latter option only works for file management, I cannot change desktop settings, typically the packet manager. The thing is it does not even open when I tried to run it. What is wrong? 

I really do not want to re-install Ubuntu, because my first problem was the X-windows did not work at all. I got around it by using "expert" install, picked LILO as loader. I have now uninstalled LILO, and Grub came back without my help...  I'm afraid re-installing  Ubuntu will set me back to the dark days of CLI only with many commands unable to run.

---

### Post by gammyhand on 2005-07-06
[QUOTE=GrootBrak]I think I should change my name to UbuntuSOD. I envy the folks that have a "trouble free" installation. I'm at the point of forgetting Linux existed.  The thing is the bits that's working make it worthwhile, so I want it all.

I have one major issue that keeps biting me back, even though I manage to work around the issues. In the desktop, I am not able to become the root user or file owner and it is a real PIA.

The package manager don't open. I cannot add or edit users. I cannot save or edit files etc etc. The "normal user" things work fine, but as soon as I tried to copy files or install or extract, I get the "no permission" bit. The only way is to use the CLI or run as different user options. The latter option only works for file management, I cannot change desktop settings, typically the packet manager. The thing is it does not even open when I tried to run it. What is wrong? 

I really do not want to re-install Ubuntu, because my first problem was the X-windows did not work at all. I got around it by using "expert" install, picked LILO as loader. I have now uninstalled LILO, and Grub came back without my help...  I'm afraid re-installing  Ubuntu will set me back to the dark days of CLI only with many commands unable to run.[/QUOTE]
 Well in regards to the package manager what is the command it is running? By default the root account is disabled in ubuntu.

My synaptic launches with: **gksudo /usr/sbin/synaptic**

For places you get no permision errors run the command as sudo (Super User Do)...

sudo cp filea fileb - that would copy file a to file b with super user (root) permissions).

---

### Post by Bl0wn2b1ts on 2005-07-06
Hi,

Could you run Users and Groups as the root user and give your regular account the permissions you need?

hope this helps

Bl0wn2b1ts

---

### Post by codejunkie on 2005-07-06
let me get this streight you can't get root access right, or you can get root access through the terminal but you can't access things like synaptic through the gui by clicking on System/Administration/Synaptic Package Manager.

---

### Post by gammyhand on 2005-07-06
[QUOTE=codejunkie]let me get this streight you can't get root access right, or you can get root access through the terminal but you can't access things like synaptic through the gui by clicking on System/Administration/Synaptic Package Manager.[/QUOTE]
No...what I said was that you should check the command that launches your synaptic. It may not be running in super user mode. I posted the command it should be above.

---

### Post by codejunkie on 2005-07-06
[QUOTE=gammyhand]No...what I said was that you should check the command that launches your synaptic. It may not be running in super user mode. I posted the command it should be above.[/QUOTE]
I was talking about the first thread i couldn't quite understand what he was asking.
but i have figured it out.

---

### Post by codejunkie on 2005-07-06
[QUOTE=GrootBrak]I think I should change my name to UbuntuSOD. I envy the folks that have a "trouble free" installation. I'm at the point of forgetting Linux existed.  The thing is the bits that's working make it worthwhile, so I want it all.

I have one major issue that keeps biting me back, even though I manage to work around the issues. In the desktop, I am not able to become the root user or file owner and it is a real PIA.

The package manager don't open. I cannot add or edit users. I cannot save or edit files etc etc. The "normal user" things work fine, but as soon as I tried to copy files or install or extract, I get the "no permission" bit. The only way is to use the CLI or run as different user options. The latter option only works for file management, I cannot change desktop settings, typically the packet manager. The thing is it does not even open when I tried to run it. What is wrong? 

I really do not want to re-install Ubuntu, because my first problem was the X-windows did not work at all. I got around it by using "expert" install, picked LILO as loader. I have now uninstalled LILO, and Grub came back without my help...  I'm afraid re-installing  Ubuntu will set me back to the dark days of CLI only with many commands unable to run.[/QUOTE]

i just remembered doing an expert install once, and having the same problems that you are having now, this is because you enabled the rootaccount/su when you set up ubuntu during the expert install and this sometimes doesn't add your user account to the sudoers file. the reason you can't use apps like synaptic from the System/Administration/ menu is because ubuntu uses sudo/gksudo by default instead of su/gksu like other linux distros. your not able to launch for example synaptic because the command in System/Administration/ menu to launch synaptic is ```
gksudo /usr/sbin/synaptic
``` and your user account is not in the sudoers file so login as root by opening a terminal typing```
su
```then enter the rootuser password it should show something like this 
```

root@ubuntu:/home/your-username #

```
now enter this in the terminal
```

export EDITOR=gedit && sudo visudo

```
now add your username to the bottem this file like this
```

yourusername	ALL=(ALL) ALL

```
here is an example of what it should look like when your done
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

[COLOR=Blue]# Members of the admin group may gain root privileges
%admin	  ALL=(ALL) ALL[/COLOR]
yourname ALL=(ALL) ALL

```
where you did the expert install if your /etc/sudoers file doesn't include the part i listed in blue, i can't remember but i think mine didn't you can just add it right under the line that says
```

root	ALL=(ALL) ALL

``` it will do the same thing save and exit that file and try synaptic in the System/Administration/ menu and enter your user password and everything should be working now, hope this helps let me know how it works for you.

---

### Post by GrootBrak on 2005-07-06
My file is the same, my username is there. And yes in the CLI I get in as root.  I tried to give my "regular" username root privelages by adding the NOPASSWD bit to my username. Still does not give me root privelages in the GIU.

It seems that the only thing that changes, is that under my username, I don't have to use sudo to run commands from within the CLI. 

Is there some program you have to run to make these changes permanent?

---

### Post by codejunkie on 2005-07-07
[QUOTE=GrootBrak]My file is the same, my username is there. And yes in the CLI I get in as root.  I tried to give my "regular" username root privelages by adding the NOPASSWD bit to my username. Still does not give me root privelages in the GIU.

It seems that the only thing that changes, is that under my username, I don't have to use sudo to run commands from within the CLI. 

Is there some program you have to run to make these changes permanent?[/QUOTE]
so you can open synaptic package manager and update your computer now right, and you just want root privliges in the gui to move/copy/change-premissions etc to files.
you can do this by adding a launcher to the desktop with the command 
```
gksudo nautilus
```just use something like Root-file-manager for the name
when you open it, if it asks for a password it will be your password not the root password when you open it click on edit/prefrences then click on the behavior tab put a check in Always open in browser windows click the close button then restart the app this will open nautilus with root privliges in browser mode so you have full access to files let me know if this helps.

---

### Post by Kvark on 2005-07-07
[QUOTE=GrootBrak]My file is the same, my username is there. And yes in the CLI I get in as root.  I tried to give my "regular" username root privelages by adding the NOPASSWD bit to my username. Still does not give me root privelages in the GIU.

It seems that the only thing that changes, is that under my username, I don't have to use sudo to run commands from within the CLI. 

Is there some program you have to run to make these changes permanent?[/QUOTE]

That NOPASSWD thing is a bad idea.

Can't you add yourself to sudoers with the "su", "export EDITOR=gedit && sudo visudo", add "yourusername	ALL=(ALL) ALL"-line way codejunkie described?

---

### Post by GrootBrak on 2005-07-07
> Could you run Users and Groups as the root user and give your regular account the permissions you need? 

No. It won't even open.

> let me get this streight you can't get root access right, or you can get root access through the terminal but you can't access things like synaptic through the gui by clicking on System/Administration/Synaptic Package Manager. 

Yes. It won't open at all. 

> you can do this by adding a launcher to the desktop with the command  

Can't add a launcher to my desktop. The step by step guide that was given to me in another thread does not apply. I don't have that apps. in the drop-down menu's.

gksudo nautilus only works for "click and drag" I can edit, but not save. I have to open a terminal window. Then switch to root, then use "gedit" to edit and save. 

Here is a silly real example: I opened GIMP from the drop down menu. Found my pictures on the Windows partition. Opened and edited it. I want to save back to windows partition, but I don't have the privelage of saving to the disk. So I have to save to my user folder that had the privelage. Then I gksudo. Click and drag the file to my windows partition. That is too exessive. Note that "User's and groups" as above won't even open. So I cannot allow myself access.

---

### Post by codejunkie on 2005-07-07
[QUOTE=GrootBrak]No. It won't even open.

 

Yes. It won't open at all. 

 

Can't add a launcher to my desktop. The step by step guide that was given to me in another thread does not apply. I don't have that apps. in the drop-down menu's.

gksudo nautilus only works for "click and drag" I can edit, but not save. I have to open a terminal window. Then switch to root, then use "gedit" to edit and save. 

Here is a silly real example: I opened GIMP from the drop down menu. Found my pictures on the Windows partition. Opened and edited it. I want to save back to windows partition, but I don't have the privelage of saving to the disk. So I have to save to my user folder that had the privelage. Then I gksudo. Click and drag the file to my windows partition. That is too exessive. Note that "[COLOR=Blue]User's and groups[/COLOR]" as above won't even open. So I cannot allow myself access.[/QUOTE]

if it's a windows xp install with a ntfs partition writing to it is disabled because it can corrupt the filesystem if it is a fat32 partition  it should write to it fine but you have to as root give your self permisions if you would open a terminal and type```
mount
``` and post the results here i will try and help you do that 
and for the User's and groups at the terminal login as root and type ```
users-admin
``` this will let you edit user permissions.

---

### Post by euzkoarima on 2006-04-27
[QUOTE=codejunkie]
here is an example of what it should look like when your done
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL

[COLOR=Blue]# Members of the admin group may gain root privileges
%admin	  ALL=(ALL) ALL[/COLOR]
yourname ALL=(ALL) ALL

```
where you did the expert install if your /etc/sudoers file doesn't include the part i listed in blue, i can't remember but i think mine didn't you can just add it right under the line that says
```

root	ALL=(ALL) ALL

``` it will do the same thing save and exit that file and try synaptic in the System/Administration/ menu and enter your user password and everything should be working now, hope this helps let me know how it works for you.[/QUOTE]

I had a similar problem, but in my case the sudoers file end at the root line. So I added de %admin line. It didn't work because the admin group wasn't defined. Finaly I add
```

%adm	ALL=(ALL) ALL

```
and all works ok.

---

