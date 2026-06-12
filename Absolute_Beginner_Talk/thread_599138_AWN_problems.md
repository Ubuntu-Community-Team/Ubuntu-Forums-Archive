---
title: "AWN problems"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by NiGHTS7041 on 2007-11-01
I have it installed and everything, however, it is giving me a lot of trouble now. For some reason I can't delete anything in my trash. The errors it gives me is that I don't have permission to erase it or something. However if I do "sudo nautilus" in the terminal and navigate to my trash folder, it is empty. I have no idea what is going on. Aslo, in opera, I can no longer view flash videos. It worked before I installed AWN. 

Thank you in advance!

---

### Post by dRock1286 on 2007-11-01
try checking the show hidden files box under 'view' (i think...not running ubuntu right now to check)...you might have hidden files in it that look like .themes or something like that with a '.' in front of the name... i had this problem once too...

---

### Post by NiGHTS7041 on 2007-11-01
Oh, nevermind about Opera. I fixed it. Well, not really. All I had to do was restart it. Haha. Seriously though, big problem still with the trash.

---

### Post by NiGHTS7041 on 2007-11-01
I did CTRL+H and nothing came up. It says I still can't delete because I don't have permission to change the parent directory.

---

### Post by dRock1286 on 2007-11-01
even when loaded in root?

---

### Post by NiGHTS7041 on 2007-11-01
Yep. I have an update though. I was able to empty my trash however there is one file that I can't delete and it's a file called "screenlets0.0.10" I installed it however I didn't like it so I deleted it. There are a whole bunch of configuration files in it and those are what I can't delete. 

If I run Sudo nautilus and type in my password then pull up my trash, it's empty. When I check view hidden files, it still says it's empty

---

### Post by dRock1286 on 2007-11-01
can you change the permissions on the individual files?

---

### Post by Partyboi2 on 2007-11-01
I think I had a a problem deleting that file after removing screenlets. I think I deleted it through the terminal and it worked.

---

### Post by NiGHTS7041 on 2007-11-01
I don't know what you mean by that or how you would do that.

---

### Post by dRock1286 on 2007-11-01
I'm not for sure...but i think you can right click on the files and choose properties.  one of the tabs might allow you to change permissions on the file...  once again though...not for sure.  Sorry if I'm of no help to you...

---

### Post by Maestro23 on 2007-11-01
> **NiGHTS7041 said:**
> I don't know what you mean by that or how you would do that.

Can you check trash from a terminal.

> cd /home/username/.Trash

ls (lists contents)

Do you see anything?

---

### Post by NiGHTS7041 on 2007-11-01
Oh no! You have been a tremendous help. Just the fact that you responded made me keep trying. So I just ended up moving the file around and playing with sudo nautilus. I then moved it to the trash again and then poof! It's gone. It's nowhere to be found so I guess my problem is solved....I just don't know how I did it. lol

---

### Post by dRock1286 on 2007-11-01
I read your link on linux is not windows and i think that everyone thinking about linux should look at that before they decide to make the switch...

---

### Post by dRock1286 on 2007-11-01
> **NiGHTS7041 said:**
> Oh no! You have been a tremendous help. Just the fact that you responded made me keep trying. So I just ended up moving the file around and playing with sudo nautilus. I then moved it to the trash again and then poof! It's gone. It's nowhere to be found so I guess my problem is solved....I just don't know how I did it. lol

well cool then.  XD

---

### Post by Maestro23 on 2007-11-01
> **dRock1286 said:**
> I read your link on linux is not windows and i think that everyone thinking about linux should look at that before they decide to make the switch...

I agree.  It amazes me how many new posts I see from new people who have jumped to Ubuntu with both feet without really doing their homework on what this OS is really is. Smart thing to do is try the live CD 1st.  Then if you want to go further, dual-boot with you existing XP.  Then play with the OS and start seeing if you can do all your taks you do in Windows in Linux.  That's just my thought process though.. maybe I'm the crazy one.:)

---

### Post by dRock1286 on 2007-11-01
> **Maestro23 said:**
> I agree.  It amazes me how many new posts I see from new people who have jumped to Ubuntu with both feet without really doing their homework on what this OS is really is. Smart thing to do is try the live CD 1st.  Then if you want to go further, dual-boot with you existing XP.  Then play with the OS and start seeing if you can do all your taks you do in Windows in Linux.  That's just my thought process though.. maybe I'm the crazy one.:)

I did what you did...I still dual-boot with xp just for programs that I know run in windows that i need for school and I don't want to mess with trying to install then uninstall them in ubuntu.  I figure that once I am done with school, I will format my xp drive and use it as a second harddrive for media files...then buy a cheap computer to run whatever flavor of windows is going at the time.

---

