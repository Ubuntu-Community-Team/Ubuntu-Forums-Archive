---
title: "Login"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by watnazn on 2007-12-30
Hey, is there a way to get rid of the login menu without having to enter the keyring password every time?

---

### Post by aidanr on 2007-12-30
In a terminal```
gksudo gdmsetup
```
Or from the menu, System -> Administration -> Login Screen
Go to the security tab and check "Enable automatic login".

---

### Post by watnazn on 2007-12-30
I know how to disable the login menu, i was just wondering if you could do it without having to type in the password for keyring every time.
Thanks though.

---

### Post by bwtranch on 2007-12-30
Not recommended my friend. The login password is one is the strengths of Unix/Linux security. A little bit of typing is better than...your losing your shirt. And don't leave any terminals open as root for any length of time as necessary for the same reason. Just a friendly word to the wise. Cheers :)

---

### Post by aidanr on 2007-12-30
> **watnazn said:**
> I know how to disable the login menu, i was just wondering if you could do it without having to type in the password for keyring every time.
Thanks though.

Oh ok, try [this]("http://ubuntuforums.org/showthread.php?t=123116") then.

---

### Post by watnazn on 2007-12-30
In [http://ubuntuforums.org/showthread.php?t=123116]("http://ubuntuforums.org/showthread.php?t=123116") . I got everything exept step 3, which is the main step. Anyone have a n0ob explanation on how to do this? Thanks

---

### Post by watnazn on 2007-12-30
i don't know how to get to /etc/X11/gdm/ because i typed sudo gedit /etc/X11/gdm/ and a blank text document opened, and you cant add a text document in a text document, so i don't know..

---

### Post by chuchan on 2007-12-30
do the following...

1. Go to menu     'System --> Administration --> login window'
2. Provide your root password
3. Go to security tab
4. Select the check box    "Enable Automatic login"
5. Select the user name which you wanted to be logged in.

Thats it!... reboot the machine; it will automatically login to the desktop......

---

### Post by watnazn on 2007-12-30
Yes, i know that, i am just trying to find out how to make it so it doesn't ask for the keyring password every time it starts up.
Thanks though.

---

### Post by aidanr on 2007-12-30
Change /etc/X11/gdm to /etc/gdm as per Gabbegubben's post in that thread.

---

### Post by watnazn on 2007-12-30
but how do i get to /etc/gdm, sorry, im a newb

---

### Post by slibuntu on 2007-12-30
On a terminal type the following, "cd /etc/gdm" , this brings you to the directory

Now you want to make a file called nopassusers.txt, do this by typing 'sudo gedit nopassusers.txt'

Now add the usernames you wish to include to that file, save the file and that should do it!

---

### Post by watnazn on 2007-12-30
thanks man, i think it worked.

---

### Post by watnazn on 2008-01-02
I got the nopassusers.txt into /etc/gdm and i put my username in the text file. But i restarted the computer and the keyring unlock still shows up. Any other suggestions on how to solve this?
Thanks.

---

