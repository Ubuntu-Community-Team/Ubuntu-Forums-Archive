---
title: "New user - vmware player question"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by gcos7 on 2007-06-12
After asking a question a couple of days ago regarding being able to run vmware in Linux, I was told I should try VMware player, as it is free.  I downloaded it and installed it, then followed the below link to try to get it to use my existing Windows XP installation, so that I didn't have to either reinstall Windows or install Windows within VMware.

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

When I click on the windows.vmx file, it starts up a window that then tells me it can't find windows.xmdk file.  The file exists in my home folder along with the .vmx file and the MBR file.  When the error occurs and I use it's browse function, I can click on my .xmdk file but it returns with the same error.  Can anyone help me on this?

I am a VERY new user, so please "be gentle".;)

---

### Post by incubus on 2007-06-12
gcos7,

I'm probably not the best person to help you (short experience with vmware), but can you check that you can open the .vmx file as a regular text file?

I'm asking this, because maybe if you post it here, we could see whether there is something wrong there.

incubus

---

### Post by dhruva023 on 2007-06-12
i would say that the xmdk file is damaged,  convert the both file again.

---

### Post by gcos7 on 2007-06-12
;)It appears to be a permissions problem, as I can log on as root, cd to my user directory and it at least starts up (I know, Ubuntu disables it, but it's simple to enable, and I wanted the access).  I haven't checked the permissions at the command line and chmod'd it yet (changing the permissions via the file system browser doesn't seem to work on it).  However, I have run into another "little" problem I'm researching on the forums to see if there is a work-around for:  Windows thinks the hardware has changed, and as a result it wants to re-activate Windows (of course I don't want to do that because then it will cause problems when I just boot Windows).  Anyone have a work around on that?

Thanks!:)

---

