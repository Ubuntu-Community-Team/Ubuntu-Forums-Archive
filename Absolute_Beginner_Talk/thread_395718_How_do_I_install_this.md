---
title: "How do I install this?"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Malik on 2007-03-28
[http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1764&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadfinder.intel.com/scripts-df-external/Detail_Desc.aspx?agr=Y&ProductID=1764&DwnldID=8203&strOSs=39&OSFullName=Linux*&lang=eng)


:confused: :confused:

---

### Post by eljalill on 2007-03-28
You need to download the .tar.gz file and extract it (Doubleclick will open the program to do that).
Then look at what you got, read the README... 
and then execute any file that looks like setup or install or so. You can double click or run ./that_file in a terminal.

More questions? Or wrong answer? Being more specific yould help...

---

### Post by Malik on 2007-03-28
theres no read me. Heres what its got inside.

[http://www.zshare.net/image/inside-png.html](http://www.zshare.net/image/inside-png.html)

---

### Post by jakev383 on 2007-03-28
> **Malik said:**
> theres no read me. Heres what its got inside.

[http://www.zshare.net/image/inside-png.html](http://www.zshare.net/image/inside-png.html)
Go to a command line in that dir, and type:
./install.sh
if it doesn't execute, you may need to switch to root and make it executable as well:
sudo chmod +x install.sh
sudo ./install.sh

---

### Post by Malik on 2007-03-28
dude I feel like such a bum on linux man. I cant even do a simple install. I dont know what im doing dude :(

---

### Post by eljalill on 2007-03-28
Lighten up :) After the 5th reinstall or so, you'll pretty much know your way around..;)
No really, that's how (nearly) everyone feels at the beginning. Someone said, it's a culture shock. That was in a really nice article about Linux and Windows, which I can't find anymore now.

But were you able to install now?

---

### Post by Malik on 2007-03-28
> **eljalill said:**
> Lighten up :) After the 5th reinstall or so, you'll pretty much know your way around..;)
No really, that's how (nearly) everyone feels at the beginning. Someone said, it's a culture shock. That was in a really nice article about Linux and Windows, which I can't find anymore now.

But were you able to install now?
no, this happend.

[http://paste.ubuntu-nl.org/12619/](http://paste.ubuntu-nl.org/12619/)

:(

---

### Post by eljalill on 2007-03-28
Well, you might want to look at the dri.log and see, what it says and/or post that here..
Contrary to windows, in Linux I actually find following the suggestions in the error messages useful..

Also "sudo apt-get update" in a terminal might help to get you to the latest versions of everything... In case you haven't updated yet.

PS: "locate dri.log" in a terminal tells you, where it is, in case you don't know

---

### Post by Malik on 2007-03-28
> **eljalill said:**
> Well, you might want to look at the dri.log and see, what it says and/or post that here..
Contrary to windows, in Linux I actually find following the suggestions in the error messages useful..

Also "sudo apt-get update" in a terminal might help to get you to the latest versions of everything... In case you haven't updated yet.

PS: "locate dri.log" in a terminal tells you, where it is, in case you don't know
i put locate dri.log 

nothing happend.

damn man why does a simple installation gotta be impossible?

---

### Post by jakev383 on 2007-03-28
> **Malik said:**
> no, this happend.

[http://paste.ubuntu-nl.org/12619/](http://paste.ubuntu-nl.org/12619/)

:(
You may need to run this first:
sudo apt-get update
sudo apt-get install build-essential

---

