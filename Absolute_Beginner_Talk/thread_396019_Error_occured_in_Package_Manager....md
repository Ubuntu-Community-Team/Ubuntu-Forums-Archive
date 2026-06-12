---
title: "Error occured in Package Manager..."
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Catfish_lolipop on 2007-03-28
My package manager isnt working....whenever i open it, this pops up " E: Type '“deb' is not known on line 34 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem."  i have know idea what i did so if anybody could help me i would appreciate it.........

---

### Post by nixclusive on 2007-03-28
Could'nt derive much from your description :-( you might want to read here: [http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

---

### Post by tonyr1988 on 2007-03-29
Open a Terminal (Applications >> Accessories >> Terminal) and type:

> gedit /etc/apt/sources.list

It will open a file in your text editor. Go to Search >> Go To Line. Type in 34 and press Enter. The line that your cursor is now in is the problem line. Could you post that line (and one line above / below it, just in case) in a reply to see what's wrong with it?

---

### Post by Catfish_lolipop on 2007-03-29
i went to gedit then searched the line and i guess that this is my problem...(the underlined is my problem)

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
_“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main”_

---

### Post by zvacet on 2007-03-29
Replace   &#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main&#8221; with 
**deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main**

---

### Post by Catfish_lolipop on 2007-03-29
it is telling me that i dont have permission to save the file.....

---

### Post by Maestro23 on 2007-03-29
> **Catfish_lolipop said:**
> it is telling me that i dont have permission to save the file.....

That directory/file is owned by root.  You will need to use "sudo" in front of your commands when you edit the file.

> sudo gedit

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Catfish_lolipop on 2007-03-29
it works now! thanks to everybody for the help......:)

---

### Post by tonyr1988 on 2007-03-29
Glad it's working for you. If you don't mind, could you edit your first post, click the "Go Advanced" button, and then check the box next to "My issue has been Resolved" (or similar)? It lets others know that your problem is fixed and just helps clean up the forums a tad.

---

### Post by Catfish_lolipop on 2007-03-30
i dont see a box that says "issues have been resolved"

---

### Post by Maestro23 on 2007-03-30
> **Catfish_lolipop said:**
> i dont see a box that says "issues have been resolved"

Believe it's at the bottom, scroll down.

---

### Post by tonyr1988 on 2007-03-30
> **Catfish_lolipop said:**
> i dont see a box that says "issues have been resolved"
After you click the Go Advanced button, the box should be right below the Title box. You have to edit the very first post of the thread to see it, though.

---

