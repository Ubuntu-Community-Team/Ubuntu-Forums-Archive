---
title: "Password dilemma?"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Cecebee on 2006-02-01
I just took my first step with Linux by installing Ubuntu 5.10 in a virtual machine on my Windows 2000 Pro. computer (32 bit AMD processor).  I used the free VMware Player to do the install and it went as smooth as silk.  Ubuntu started up beautifully and I got a pop up saying that there was a newer version or an update available.  I clicked on the update icon and that took me to a password entry dialog box.  Since I hadn't seen any previous mention of a password for Ubuntu I assumed it wanted my Windows login password so I entered it and that failed.  I found the place to add new users and passwords on the menu bar and went there but got the same result.  I also tried just ignoring the password box but that also didn't work.

Is there some default password that ships with the installation package?  From what I see of the Ubuntu interface it is a really good looking OS but I haven't been able to find any help for this first problem anywhere.

TIA for any responses.

---

### Post by tseliot on 2006-02-01
The password should be the following (I'm not sure because my memory is in bad shape ;) ):
```
ubuntu
```

---

### Post by void_false on 2006-02-01
Type the passwd that you entered during installation.

---

### Post by MartinJ on 2006-02-01
If you downloaded the pre-built Ubuntu vitual machine from the VMware website the password is "vmware".  Not too sure if you did this but it helps to know anyway.

---

### Post by Cecebee on 2006-02-01
Thanks guys.  Actually I had already tried "ubuntu" (lower case without quotes) and it doesn't work.  As for the password used during install, no password was asked for or required apparently.

I did download the package from VMware so I just tried "vmware" with no luck so I tried "VMware" and that also failed.

Anyone else have an idea?

---

### Post by Cecebee on 2006-02-01
Problem solved!  It turns out that "ubuntu" was the correct answer.  On my first  encounter,  I went into Users and Passwords and had guessed that the password for user Ubuntu might be "ubuntu" so I entered it and changed the password to one of my own.  It appeared to take but when I went back to the desktop and used the new password it wasn't recognized, nor  was "ubuntu".

After reading the replies here I restarted Ubuntu in its virtual machine and tried the suggested passwords and as I said earlier they didn't work.  Then the light finally came on and I entered the new password I had put in the system and sure enough it worked.  I guess the re-boot was needed to make the change register.

Thanks again for all the help.

---

