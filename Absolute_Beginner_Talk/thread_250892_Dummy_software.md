---
title: "Dummy software"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by owenb@theofficenet.com on 2006-09-04
I started using a tutorial, "LinuxCommand.org. No problem with the tutorial but I am concerned about screwing up the installed copy of Kubuntu software on the computer.
  My concern is that by using the terminal I will make a mistake and screw up the whole setup.
  As it takes me forever to install updates with my dialup modem I hesitate continue with the tutorial.
  Is there any type of "dummy" software that emulates a Linux package and will not effect the operating system?  I can use other computers with Mandriva One, Win 2000 and WinXP if necessary.
Thanks, 
         Owen

---

### Post by steve.horsley on 2006-09-04
Here's the best thing to do. Use System->Administration->Users and Groups to creat a new user. You can log in as that user (dummy perhaps?) and do anything you please. That user is totally incapable of damaging the system. He can't even use sudo to gain extra priviledges unless you add him to the admin group.

Here's a neat trick: Use Alt-Ctrl-F1 to get a text window. Log in as dummy and then enter the command:
**startx -- :1**
And you get a new graphical display for dummy. You can flip between your normal user screen and dummy's screen using Alt-Ctrl-F7 and Alt-Ctrl-F8.

P.S. 
Even as your normal user, you can't screw up the system unless you use **sudo** in front of each command to gain admin rights.

---

### Post by apiper on 2006-09-04
What ^^he^^ said.

Plus, I've had a quick peek at the table of contents for that tutorial and you'll have gotten all the way to section 4 of chapter 7 before you gain the (temporary) power to alter system files, so I think that you'll be perfectly OK with your existing Kubuntu installation.

Just because the terminal is a powerful tool doesn't mean its to be feared. I reckon you'll be just fine - you strike me as a cautious fellow ;) 

If you have a DVD or CD burner and want to be *extra*-safe, you could go find all the updated packages that you've downloaded and burn them to CD or DVD, so if the worst really does happen then you won't have to re-download them.

(The updated packages live in the /var/cache/apt/archives directory, and yes some of them do have slightly strange names with %'s in them)

Good luck!

---

### Post by owenb@theofficenet.com on 2006-09-06
> **steve.horsley said:**
> Here's the best thing to do. Use System->Administration->Users and Groups to creat a new user. You can log in as that user (dummy perhaps?) and do anything you please. That user is totally incapable of damaging the system. He can't even use sudo to gain extra priviledges unless you add him to the admin group.

Here's a neat trick: Use Alt-Ctrl-F1 to get a text window. Log in as dummy and then enter the command:
**startx -- :1**
And you get a new graphical display for dummy. You can flip between your normal user screen and dummy's screen using Alt-Ctrl-F7 and Alt-Ctrl-F8.

P.S. 
Even as your normal user, you can't screw up the system unless you use **sudo** in front of each command to gain admin rights.
Thanks Steve, 
I did follow through on your suggestion of going to Administration->Users and Groups to add a new user. Unfortunately the new user "dummy" does not appear as a option when logging on.
I tried editing it in but still didn't work.  Any suggestions?
Owen

---

### Post by steve.horsley on 2006-09-06
Don't you get a "Username: " prompt when Ubuntu boots up? I don't understand this - what do you see when it boots?

---

### Post by owenb@theofficenet.com on 2006-09-07
When I boot up I ket the Kubuntu sign in menu with Username "owen" as the default.  The Password: is left blank.

There is a submenu with options; one of which is "Switch User"'
This option has a check box which is already checked. The option also has "unused (:0,vt7). Choosing this menue item does nothing but returns me to the Kubuntu sign in menu.

Since my previous response I have gone back into System->Administration->Users and Groups and changed the new "dummy" account's "Primary Group" from "dummy", (which had been set by default) to "owen". (To do this I had to go to "administrator mode").

At this juncture I logged out and rebooted. The default login menue still had "owen" and the "Switch User" remained as stated above.
 What I then did was deleated "owen" from "Username" and substituted "dummy". I also typed in the password for the "dummy" account.
  The booting process proceeds normally, except there is a error message. "Error-KDesktop" "The process for the protocol died unexpectedly"
   Clicking on the "OK" brought up another KDesktop error.  "The process for the media protocol died unexpectedly"
    Clicking on the "OK" brought me to the default KDE menu screen. Chosing "Konsole" from the "System" menu verified that I was "dummy@owen-laptop:~$"

  I haven't tried any of the other installed software/ programs so far. I don't know what to do about the error messages; if anything if it doesn't effect the rest of the system /software.
Thanks again,
              Owen

---

