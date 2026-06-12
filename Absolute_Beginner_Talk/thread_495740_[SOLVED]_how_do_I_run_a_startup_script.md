---
title: "[SOLVED] how do I run a startup script?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by zmike1 on 2007-07-08
I´m trying to ¨fix¨ my right-Alt key (to make it behave like the left-Alt key) and it seems from

[http://www.linuxquestions.org/questions/showthread.php?p=2611981](http://www.linuxquestions.org/questions/showthread.php?p=2611981)

that putting a script file somewhere to run something that changes xmodmap will meet the need.

How/where do I put such a script file that will run at startup?

If there is an easier or better way, I´m open to it.  My original question to the forum:

[http://ubuntuforums.org/showthread.php?t=495297](http://ubuntuforums.org/showthread.php?t=495297)

---

### Post by isaacj87 on 2007-07-08
Well, technically, you can put the script in your home folder.

Make it executable:

Right click->Properties->Permissions Tab->and then check the box that says "Allow executing file as program"

then add it to your sessions to make it start on start-up

System->Preferences->Sessions

Make a new startup and just put the script in there. For example, if I had a compiz script I would do this:

Name: Compiz

Command: /home/YOURNAME/compiz_startup.sh

remember the .sh at the end

---

### Post by zmike1 on 2007-07-08
> **isaacj87 said:**
> Well, technically, you can put the script in your home folder.

Make it executable:

Right click->Properties->Permissions Tab->and then check the box that says "Allow executing file as program"

then add it to your sessions to make it start on start-up

System->Preferences->Sessions

Make a new startup and just put the script in there. For example, if I had a compiz script I would do this:

Name: Compiz

Command: /home/YOURNAME/compiz_startup.sh

remember the .sh at the end

Thanks for the reply.  Do I understand correctly that putting the ¨ScriptName_startup.sh¨ will make the script run if it´s in my /home/myname folder?  (after setting permission)??

This is all very new to me.  
About the adding it to my sessions, I do not seem to have what you wrote as an option.
Since I´m running xubuntu I don´t have a system->preferences->sessions as far as I can tell.  INstead I have a ¨sessions and startup¨ option that doesn´t seem to allow for adding scripts.  I must be missing something basic...  My ¨sessions¨ option looks like:

(sorry for the ugliness...)

---

### Post by isaacj87 on 2007-07-08
OH...jeez...sorry I didn't know you had Xubuntu...sorry but it's a different beast for me...I run regular Ubuntu with GNOME. Let me do a little searching for you and I'll see if I can help you better...but I'm sure adding something to sessions isn't that much different in Xubuntu.

EDIT: And about your question about the scripts...remember you don't need the underscore ( _ ) unless it's actually in the name of the script. If it happens to be, for example, compiz.sh, then compiz.sh is the name. If it happens to be compiz_startup.sh, then that's its name. You can keep it simple and call it keyboard.sh or keyboard_startup.sh for your particular script. If you want to simplify adding the script to sessions you can easily move the script to  /usr/local/bin. Let me get back to you about sessions for Xubuntu and I'll give you a detailed explanation about all of this. :)

---

### Post by zmike1 on 2007-07-08
Thanks again.  All of linux is a different beast for me....  but I´m learning.  Sl-o-o-oo-w-ly.....

---

### Post by kerry_s on 2007-07-08
xubuntu> menu> settings>autostart
is the same as gnome session startups

---

### Post by zmike1 on 2007-07-08
Thank you.  So, that option gives me a panel with three blanks: Name, Description, and Command.  From what is already there, it appears that Name and Description are simple explanations of what will be run and Command is what does the running.

So, is this (Command) the place where I should put something like:

       /home/myname/run_file.sh

where run_file is the script that I wrote and made executable?

---

### Post by isaacj87 on 2007-07-08
yup...that would be the easiest way...make sure to make it executable

---

### Post by zmike1 on 2007-07-08
Thank you, both.  I think I´ll be able to get through it now.    :)

---

