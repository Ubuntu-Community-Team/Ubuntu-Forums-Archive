---
title: "Flash for linux"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by Arthur Millar on 2006-07-02
Im have found Flash for linux on the net and i was wondering if this works on Ububtu dd6.06

[http://f4l.sourceforge.net/](http://f4l.sourceforge.net/) 

if so how do i install it?
i downloaded (f4l_beta_swfExport) from source forge 
 [http://sourceforge.net/project/showfiles.php?group_id=87799](http://sourceforge.net/project/showfiles.php?group_id=87799)  	

but i have no idea how to install 

AMD 64 bit user

---

### Post by ajgreeny on 2006-07-02
Flashplugin-nonfree is available in the repos already, but you need to use the multiverse repositories to find it.  Go to this site for more details.
[https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096)

---

### Post by ahaslam on 2006-07-02
I used [**this**]("http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash") and had no problems (quick, easy & effective).

Tony.

Sorry, I didn't follow your link. I assumed it was another question about the plugin.
It looks interesting, Don't see why it wouldn't work.

Tony.

---

### Post by Arthur Millar on 2006-07-02
im talking about the design package
if you follow my first link you will see

---

### Post by Roger Mudd on 2006-07-02
I don't think Arthur was referring to a Flash player. The link he provided led me to a Flash creation tool similar to Macromedia/Adobe Flash. I may be mistaken, but if not, I'm intrigued.
Can't help you with the install myself, but you may want to post here:

[http://sourceforge.net/forum/forum.php?forum_id=301386](http://sourceforge.net/forum/forum.php?forum_id=301386)

---

### Post by Arthur Millar on 2006-07-02
thanks
if any one would like me to explain (after i succeed!)
i will send the post link

---

### Post by ahaslam on 2006-07-02
Extract the file & open a terminal, cd to the extracted dir, then:
./configure
make
sudo make install

PS. If you've not done this before, you may need this first:
sudo apt-get update
sudo apt-get install build-essential

**IGNORE - I'M WRONG - I CAN'T INSTALL EITHER!**

---

### Post by Arthur Millar on 2006-07-02
hey Ant
after doing the apt-get commands you gave me and extracting the F4l folder to my home folder  the folder is called f4l 
i type  
artnlaw@HomePC:~$ cd /artnlaw/F4l
i get 
bash: cd: /artnlaw/F4l: No such file or directory

what am i doing wrong

---

### Post by ahaslam on 2006-07-02
[QUOTE=Arthur Millar]i type  
artnlaw@HomePC:~$ cd /artnlaw/F4l
i get 
bash: cd: /artnlaw/F4l: No such file or directory[/QUOTE]
If it's in your home folder it would be, 'cd f4l-0.2.1'

Anyway, this doesn't look like a standard install. 
I made an assumption with my first post here, and I've done it again. I guess that I'm an ***!
Just looked at one of the readme's and it looks as though something called 'CMake' is required to compile. Here's the web site: [http://www.cmake.org/HTML/Index.html](http://www.cmake.org/HTML/Index.html)

Sorry I cant help,

Tony (the ***). :oops:

---

### Post by Arthur Millar on 2006-07-02
no worries thanks 
are you intrested in use f4l
if so i will try to make it work
i renamed the folder to f4l (lazy)

---

### Post by ahaslam on 2006-07-02
[QUOTE=Arthur Millar]no worries thanks 
are you intrested in use f4l
if so i will try to make it work
i renamed the folder to f4l (lazy)[/QUOTE]
Inkscape & GIMP are more than enough for my simple needs. 
To get more help, I'd post a new thread with a more specific title (to avoid assumptions like mine).

Good luck,

Tony.

PS. I would post under 'Desktop Support' (it's a little beyond 'absolute beginner talk') - you may have to wait a bit longer for a response, but it should attract the right people.

---

