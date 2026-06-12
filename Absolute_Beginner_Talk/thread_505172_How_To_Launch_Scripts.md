---
title: "How To Launch Scripts"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by TechieZero on 2007-07-20
How do you launch a script from a desktop icon with an option like start or stop?

---

### Post by ramjet_1953 on 2007-07-20
Firstly make sure your script is executable, by right clicking on it and choose [COLOR="Blue"]Properties[/COLOR]

Click on the [COLOR="Blue"]Permissions[/COLOR] tab and make sure that there is a tick in the [COLOR="Blue"]Execute[/COLOR] box.

Also, make sure that the script has a [COLOR="Blue"].sh[/COLOR] suffix. ie [COLOR="Red"]myscript.sh[/COLOR]

To then run it simply type this into a terminal [COLOR="Red"]sh myscript.sh[/COLOR]

Regards,
Roger :cool:

---

### Post by TechieZero on 2007-07-20
> **ramjet_1953 said:**
> Firstly make sure your script is executable, by right clicking on it and choose [COLOR="Blue"]Properties[/COLOR]

Click on the [COLOR="Blue"]Permissions[/COLOR] tab and make sure that there is a tick in the [COLOR="Blue"]Execute[/COLOR] box.

Also, make sure that the script has a [COLOR="Blue"].sh[/COLOR] suffix. ie [COLOR="Red"]myscript.sh[/COLOR]

To then run it simply type this into a terminal [COLOR="Red"]sh myscript.sh[/COLOR]

Regards,
Roger :cool:

Thanks for the reply.

I got the script to execute using ./example.sh option1 --- or --- sh example.sh option1 --- however I have to change directories to the directory where the script is located then issue the command. BTW - what is "./" called anyway?

What I would like to do is create an ICON on the desktop bar that I can simply click and it does all of this. Any suggestions?

---

### Post by TechieZero on 2007-07-20
Bah! I wish I was home to try this out, but I bet I can use the launcher to kick it off w/ the sh command!

---

### Post by Skrynesaver on 2007-07-20
May I suggest creating a $HOME/bin directory where you put all your scriupts.
Now add this to your path in $HOME.bashrc like so
```

echo 'export PATH=$PATH:$HOME/bin'>>$HOME/.bashrc

```
Your script is now a fully fledged command that you can user irrespective of your current working directory.
Now if the script is executeable, see ramjet's post above then you can drag the script to the toolbar and it will appear as an icon, then right click for properties and select an icon image of your choice

---

### Post by TechieZero on 2007-07-20
> **Skrynesaver said:**
> May I suggest creating a $HOME/bin directory where you put all your scriupts.
Now add this to your path in $HOME.bashrc like so
```

echo 'export PATH=$PATH:$HOME/bin'>>$HOME/.bashrc

```
Your script is now a fully fledged command that you can user irrespective of your current working directory.
Now if the script is executeable, see ramjet's post above then you can drag the script to the toolbar and it will appear as an icon, then right click for properties and select an icon image of your choice

Thanks for the reply. I will give this a shot when I get home. Will I be able to add a command line option to the call in the properties? Do I simply place it at the end?

---

### Post by TechieZero on 2007-07-20
This worked! I am so happy! Thank you all!!!

---

