---
title: "Manual Install upgrade -no synaptic -feisty -where to install"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-05-06
Ok, I have a couple questions.  I am running Fesity

I installed Juploadr (for flickr) and there is currently a new version that I want to upgrade to. This is not found in any of the resaprositories.

Someone was kind enough to make me a .deb to get it to go in when I was even "newer" However now I am stuck again.  I have tried psychocats and a few other sites for manual installs, but no luck

1) do I need to uninstall the old program before i put in the new version

2) where do I put the program files (more specifically what directory do I put new programs in), I work off of my desktop but I know they go else where (ie program files is what I am used to)

3) how in the world do you get a .tar.gz to work for you?

THX
:confused: :confused: :confused:

---

### Post by zvacet on 2007-05-07
**pprograms>accessories>terminal**

go to the directory where you downloaded program

```
tar zxvf program_name
```

program_name= exact name of program you want to install

This will create folder in wich is **read me** file and that file wil tell you all you have to do to install program

---

### Post by Sef on 2007-05-07
> 
Code:

tar zxvf program_name

program_name= exact name of program you want to install

This will create folder in wich is read me file and that file wil tell you all you have to do to install program

Another option would be to right click and go to extract here.

---

### Post by mkjarema on 2007-05-07
Thank you very much for the assistance.  However, I know where the terminal is, I know how to extract here.

My question is 

In what folder (directory) do I place the files?  Is linux organized like MS in that way where there is one centralized location for program files?

In reference to updating programs, do I need to remove the old one first?  

I am still having troubles installing manually .tar.gz etc.  

These are the few problems that make me question Ubuntu.  Synaptic is awesome, but if a program or the version of a program you want isn't in there, it should be difficult to install yourself.

Thanks again

---

