---
title: "Menu Editor trouble"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by phil54601 on 2007-01-26
Hello;
    I'm fairly new to Ubuntu 6.06LTS, so am probably missing something VERY basic, I have tried numerous times to display most of the programs under the 'Applications/SystemTools/ menu,  The SystemTools/ menu showed up after I installed parallels. I have used both the drop down menu and the right click methods to start the editor.  After ticking the desired programs.  I shut down & restarted (reboot).  The menu was still at the default level.  In other words nothing was changed - my menu items were  still NOT visble!
 I even tried 'sudo alcarte'.  The same result. 
Please explain what I doing wrong?
ThankYou.
Phil

---

### Post by ComplexNumber on 2007-01-26
> **phil54601 said:**
> Hello;
    I'm fairly new to Ubuntu 6.06LTS, so am probably missing something VERY basic, I have tried numerous times to display most of the programs under the 'Applications/SystemTools/ menu,  The SystemTools/ menu showed up after I installed parallels. I have used both the drop down menu and the right click methods to start the editor.  After ticking the desired programs.  I shut down & restarted (reboot).  The menu was still at the default level.  In other words nothing was changed - my menu items were  still NOT visble!
 I even tried 'sudo alcarte'.  The same result. 
Please explain what I doing wrong?
ThankYou.
Phil
just a haunch, but would you mind firing up your terminal and entering "cd  */home<your-username>/.local/share/applications"*(without the quotes) and telling me if there is anything that is owned by root?

---

### Post by phil54601 on 2007-01-26
Hello;
   I tried this command ' cd /home/phil/.local/share/applications ' in the terminal window.  The result was 'Permission denied'.
There are lots offiles & directories that is owned by root.  That from looking nautilus.
More hand holding I'm afraid.
Thanks In Advance.
Phil

---

### Post by ComplexNumber on 2007-01-27
> **phil54601 said:**
> Hello;
   I tried this command ' cd /home/phil/.local/share/applications ' in the terminal window.  The result was 'Permission denied'.
There are lots offiles & directories that is owned by root.  That from looking nautilus.
More hand holding I'm afraid.
Thanks In Advance.
Phil
then thats where the problem is. it should not be owned by root, but for some reason, it suddenly becomes owned by root and the user can't user the menu editor and some entries don't show up.
to solve the problem, just fire up the terminal and type in 'sudo chown -R PHIL:PHIL /home/phil/.local/share/applications'.


NOTE: because the stupid smilie system on this forum keeps on turning everything that is 'semicolen p' into this : :p, i can't write 'phil semicolon phil'. therefore, please write 'PHIL:PHIL' in lowercase instead because thats the way its meant to be

---

### Post by phil54601 on 2007-01-27
Hello ComplexNumber;
     I tried your suggestion.    I did reboot.  Do I need to, I thought these changes were instant?
  Nothing changed.  The parallels program is the only thing visible in the 'System Tools' sub menu. Permission is still denied for this command:  
 'cd /home/phil/.local/share/applications'.
If I use sudo su, then I can change to that directory.

This command with the second 'Phil' changed to 'phil' :     
 'sudo chown -R phil:Phil /home/phil/.local/share/applications'  
seems to have no effect.  Is it possible that parallels is resetting the owner on every reboot?

   To use alacarte all I need to do is tick the item I want visble & close the menu editer, correct?   I even tried 'sudo alacarte' in a terminal with no success.
Thanks again.
Phil

---

### Post by ComplexNumber on 2007-01-27
> Nothing changed. The parallels program is the only thing visible in the 'System Tools' sub menu. Permission is still denied for this command: 
 'cd /home/phil/.local/share/applications'.in that case, try 2 levels above that. ie 

'sudo chown -R PHIL:PHIL /home/phil/.local'


NOTE: same as before, put the lower case version of "PHIL:PHIL" in.

btw you didn't need to reboot.

---

### Post by phil54601 on 2007-01-27
Hello ComplexNumber;;
I tried this command:  
sudo chown -R PHIL:PHIL /home/phil/.local
with the lowercase  name.
The option worked I now can change my applications menu.
THANK YOU VERY MUCH.
Phil

---

### Post by leona on 2007-02-05
Wow thanks, that was the problem for me, just wanted to say thanks my .local was owned by root, another one of those lovly Ubuntu bugs a :)  Thanks my menu works correctly again now :)

---

### Post by kenmiles on 2007-02-10
Thanks from me also, this has had me bugged for a couple of weeks.
Regards, Kenneth.

---

