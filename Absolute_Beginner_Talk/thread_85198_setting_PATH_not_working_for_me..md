---
title: "setting PATH not working for me."
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by sreg0r on 2005-11-02
I'm having trouble getting set PATH to work for me using Kubuntu 5.10
i have downloaded and installed finstall which installs foldingathome and it comes with a utility called folding.  if i am in the directory where it is installed i can type ./folding status and it will tell me the foldingathome status on the computer.

What i wanted to do is be able to type "folding status" when in any folder from BASH.  trying to do this i typed
PATH=/~/foldingathome/:$PATH
export path

then i typed folding status I got a "folding: command not found" error.
what i wanted to know is if someone could tell me how to achieve what i am trying and also how i can remove directorys from PATH.
thanks.

---

### Post by ngms27 on 2005-11-02
You have to do it in .bashrc in your home directory. No need for the export statement.

JonnyT

---

### Post by Ramses on 2005-11-02
[Here]("http://www.troubleshooters.com/linux/prepostpath.htm") is information about path-variable.

I don't know if this is correct way but you could also make symbolic link of this folding program to /usr/bin. 

```
sudo ln -s ~/foldingathome/folding /usr/bin/folding
```

This method leaves the link to /usr/bin after you have uninstalled the program, but i don't think it is such a big deal.

---

### Post by sreg0r on 2005-11-02
alirght i think i have it figured out now.  Thanks Ramses for your advice as it worked out.  The only problem with that method is that i would have to do it for each file, where as PATH could specify a whole directory.  
I get the PATH method to work, the problem was the / before the ~.  I also got it to work with alias folding="~/foldingathome/folding"
Now i have lots of incorrect folders in my PATH that i want to get rid of, does anybody know how to get rid of them without having to type everything in again?

---

### Post by Ramses on 2005-11-02
If you haven't made any changes to .bash_profile and .bashrc files i think your path variable will be back to normal if you logout and login.

from [http://www.troubleshooters.com/linux/prepostpath.htm#_singleuser]("http://www.troubleshooters.com/linux/prepostpath.htm#_singleuser")

To add a directory to the path of a single user, place the lines in that user's .bash_profile file. Typically, .bash_profile already contains changes to the $PATH variable and also contains an export statement, so you can simply add the desired directory to the end or beginning of the existing statement that changes the $PATH variable.

---

### Post by thieves.honor on 2005-11-03
i'm having the same problem.  i installed java in my home directory.  i edited my .bash_profile to add PATH=~/home/Programs/jdk/jre/bin/:$PATH.  after logging out and logging back in the echo $PATH command does not show the added path to the jre bin.  any suggestions??

---

### Post by Ramses on 2005-11-06
Did you add 'export PATH' command after your path line in .bash_profile?

---

