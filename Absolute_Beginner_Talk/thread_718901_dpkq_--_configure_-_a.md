---
title: "dpkq -- configure - a"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by bjhome on 2008-03-08
i am getting this message and am being told to run it. how and where do i go to do this. step by step instructions please. new to this.and which is the better and easiest to use limewire or frostwire. these are what i was trying to load when this happened.

---

### Post by taurus on 2008-03-08
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

Frostwire is better but before you can use it, make sure you have sun java installed on your machine or it will not run.

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> i am getting this message and am being told to run it. how and where do i go to do this. step by step instructions please. new to this.and which is the better and easiest to use limewire or frostwire. these are what i was trying to load when this happened.

Open up a terminal screen found in  Applications menu>Accessories>Terminal

Then, inside the terminal type:
```
sudo dpkg --configure -a
sudo apt-get update
```

It will ask for your password.  Type it in, but understand you won't see the password while typing.  Then hit the enter key...  

It seems like you may have inturrupted the package manager during an installation...

---

### Post by crjackson on 2008-03-08
> **taurus said:**
> Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
```

Frostwire is better but before you can use it, make sure you have sun java installed on your machine or it will not run.

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

Taurus, wow.. you are quick on the keys...  Oh well, I provided redundant information...

---

### Post by bjhome on 2008-03-08
now i am getting" command not found" where do i go from here and yes i canceled the download because it was taking a long time. thought id go back to it later. but that was not to be.

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> now i am getting" command not found" where do i go from here and yes i canceled the download because it was taking a long time. thought id go back to it later. but that was not to be.


Sounds like you made a typo in the syntax.  Just cut / past the code from the post.

---

### Post by bjhome on 2008-03-08
now i am getting      'command not found'   what do i do with this?????

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> now i am getting      'command not found'   what do i do with this?????

Could you cut / paste the command into the terminal, then when you get the error, copy all the text displayed in the terminal window and post it back?

---

### Post by taurus on 2008-03-08
Can you post the exact command that you typed in at a terminal and the whole error output?

---

### Post by bjhome on 2008-03-08
does it take a while for the sun java to load

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> does it take a while for the sun java to load

Depends on your connection...  I take it that it's working now?

---

### Post by bjhome on 2008-03-08
the sudo configuration has now worked by cutting and pasting it. thanks a million. now i am waiting for the sun java to load .

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> the sudo configuration has now worked by cutting and pasting it. thanks a million. now i am waiting for the sun java to load .
you are welcome.  I often fat finger the keyboard myself and always use cut/paste...

---

### Post by bjhome on 2008-03-08
yea the connection is good. i think . can surf the net quite fast.

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> yea the connection is good. i think . can surf the net quite fast.

It will be done shortly, you are installing more than one item.  Just sit back and let it do it's thang... :)

---

### Post by bjhome on 2008-03-08
i have a blue screen which is saying configuring sun-java6-jre and is a license page waiting for me to click ok . but will not let me click ok so i am assuming it is still configuring and will let me click the ok when it is ready.

---

### Post by bjhome on 2008-03-08
lol .....once again thanks alot.

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> i have a blue screen which is saying configuring sun-java6-jre and is a license page waiting for me to click ok . but will not let me click ok so i am assuming it is still configuring and will let me click the ok when it is ready.

use your tab key to navigate to the okay button and press the enter button on the keyboard...

---

### Post by crjackson on 2008-03-08
> **bjhome said:**
> lol .....once again thanks alot.

When your done and it's working, please mark the thread as solved and click the yellow star next to the quote button on your way out of the door :)

Thank you for shopping at ubuntu   :guitar:

---

### Post by bjhome on 2008-03-08
Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by bjhome on 2008-03-08
i now have the above page just sitting there not really doing anything, is this still loading or do i need to do something else. been there for 5-6 hours now. i am trying to download sun java

---

### Post by taurus on 2008-03-08
Use the Tab key to highlight the <OK> at the bottom and then hit the Return key to except the license.

---

### Post by bjhome on 2008-03-08
sorry didnt see your comment about the tab key. done and thanks again

---

### Post by bjhome on 2008-03-08
now i have a frostwire page thatt wont open.how can i move it form my screen? and has this finished loading java or have i tried to open frostwire prematurely.
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) feisty/multiverse sun-java6-plugin 6-00-2ubuntu2 [1392B]
Fetched 1392B in 0s (6341B/s)     
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 
dpkg: serious warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.
105688 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
Preparing to replace sun-java6-bin 6-00-2ubuntu2 (using .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Unpacking replacement sun-java6-bin ...
Selecting previously deselected package sun-java6-plugin.
Unpacking sun-java6-plugin (from .../sun-java6-plugin_6-00-2ubuntu2_i386.deb) ...
Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...

Setting up sun-java6-plugin (6-00-2ubuntu2) ...

owner@acer:~$

---

### Post by taurus on 2008-03-08
You mean you cannot kill frostwire window with the x in the upper right corner?

Otherwise, kill it from a terminal.

```
killall frostwire
```

---

### Post by bjhome on 2008-03-08
there is no x it is like a download screen and it is frozen there over top of everything.

---

### Post by taurus on 2008-03-08
Can you open a terminal from the menu, Applications -> Accessories -> Terminal?

---

