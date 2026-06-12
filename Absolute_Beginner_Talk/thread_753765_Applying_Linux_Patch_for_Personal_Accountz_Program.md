---
title: "Applying Linux Patch for Personal Accountz Program"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Andavane on 2008-04-13
I am bringing in a post from the Personal Accountz Forum as I've received no suggestions from there.
+ + + + + ++ +

When I double-clicked on this update I had the following message:
"Could not open PersonalAccountzPatch-LX32.bin
gedit has not been able to determine character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again".

gedit is a simple word processor so that is not the issue.

Personal Accountz itself has opened flawlessly on Ubuntu 7.10, Gutsy Gibbon.
It runs from double-clicking, or making a launcher, but double clicking doesn't work here.

Any ideas?

Regards

John

---

### Post by talsemgeest on 2008-04-13
It just means that the text in the file is not of a type that gedit recognizes. Try opening a binary file and you will get the same error. If it is an executable file, right click the file, go to the permissions tab and check "allow opening this file as a program."

Hope this helps :)

---

### Post by Andavane on 2008-04-13
> **talsemgeest said:**
> It just means that the text in the file is not of a type that gedit recognizes. Try opening a binary file and you will get the same error. If it is an executable file, right click the file, go to the permissions tab and check "allow opening this file as a program."

Hope this helps :)

duh!....
That's it.
It did the trick.
Thanks mate, I shouldv'e been able to work that out for myself!   :redface:

John

---

### Post by talsemgeest on 2008-04-13
No problem, glad I could help,

Just don't forget to mark this thread as solved...

---

### Post by Andavane on 2008-04-13
> **talsemgeest said:**
> No problem, glad I could help,

Just don't forget to mark this thread as solved...
Consider it done...   ):P

---

### Post by Andavane on 2008-06-17
> **talsemgeest said:**
> No problem, glad I could help,

Just don't forget to mark this thread as solved...

No I am afraid I have to open the thread up again.
In a nutshell, feisty was a problem, I could install it in gutsy fine in the end.
But Now in Hardy Heron, I am getting the message when I double-click:
"Couldn't display "/home/andavane/PAZ/paz_install.3.bin"
And in my permissions I have everything set to execute.
Hunting through the existing posts on this matter, I see that java is required.
I have downloaded the "Linux 32 bit + Java" version, and read that I need java. However there are so many Java things in the synaptic package manager, that I am at sea as to what the appropriate ones are here :-(

Everything was working fine in Gutsy. If I can't get this going, I will need to install it again.
Regards
John

---

### Post by Andavane on 2008-06-17
PS:
I have Personal Accountz up-and-running in my laptop (Gutsy) so feel it could be useful for making comparisons.

---

### Post by talsemgeest on 2008-06-17
Once you have installed java you should be able to type something like ```
java /home/andavane/PAZ/paz_install.3.bin
``` or whatever javas command is.

---

### Post by Andavane on 2008-06-17
> **talsemgeest said:**
> Once you have installed java you should be able to type something like ```
java /home/andavane/PAZ/paz_install.3.bin
``` or whatever javas command is.
Thank you.
Typing this into the command line, I get:

> andavane@asus-pc:~$ java /home/andavane/PAZ/paz_install.3.bin
Exception in thread "main" java.lang.NoClassDefFoundError: .home.andavane.PAZ.paz_install.3.bin
   at gnu.java.lang.MainThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: .home.andavane.PAZ.paz_install.3.bin not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at gnu.java.lang.MainThread.run(libgcj.so.81)
andavane@asus-pc:~$ 


Does this mean anything to you?

Regards

John

---

### Post by talsemgeest on 2008-06-18
I got nothing I'm afraid...

---

### Post by Andavane on 2008-06-18
> **talsemgeest said:**
> I got nothing I'm afraid...

Well thanks anyway.
I get the hunch that I may install Hardy again, don't know why.
At bootup earlier I had the message
"configuring network interfaces.
rc2 main process (4604) killed by SEGV dignal"
in the black and white letters.

After that, nothing whatever would respond, so it was necessary physically to turn the machine off and start again.

Yesterday there was a notice that a "recursive fault had been fixed", after which it froze again and again it was necessary physically to switch the machine off.

I wonder if anyone has some ideas... ?

Kind regards

---

### Post by robinPain on 2008-07-14
You need to rename it without the .bin extension e.g. if it was called

Personal_Accountz32.bin

then rename it to

Personal_Accountz32

Then the double-click will run it OK.

(Likewise the shortcut that it creates, rename that too without the .bin)

---

### Post by Andavane on 2008-07-14
> **robinPain said:**
> You need to rename it without the .bin extension e.g. if it was called

Personal_Accountz32.bin

then rename it to

Personal_Accountz32

Then the double-click will run it OK.

(Likewise the shortcut that it creates, rename that too without the .bin)

Robin, thank you.
The accountz program is on another machine -- I had to leave it and go back to this old one. I need assistance to connect all the wires and things up: When I have that done, I will try it (keep fingers crossed) and flag this topic and let you know. It may not yet be for a day or two.

If I can't use my accountz program, I may as well not have access to the machine. There was a work-a-round: I could reboot into Vista and work the program from there... but all those flashing things muddle me :confused:
 & hard drive goes nine-to-the-dozen checking for bugs and goodness knows what.

Will surely revert and let you know.

Thanks

Regards

John

---

