---
title: "creation vs. evolution"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by rgp-02 on 2007-02-08
evolution email not working. i believe i screwed up the setup and want to start over, but i don't know how to start the setup over. any suggestions?

---

### Post by 23meg on 2007-02-08
How exactly is it not working? Does it not start up at all? Do you get any error messages when you try to run it from a terminal?

---

### Post by rgp-02 on 2007-02-08
in terminal i got:

Password:
CalDAV Eplugin starting up ...

(evolution-2.8:4834): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.8:4834): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.8:4834): DEBUG: mailto URL command: evolution %s
** (evolution-2.8:4834): DEBUG: mailto URL program: evolution

** (evolution-2.8:4834): WARNING **: could not get system bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by rgp-02 on 2007-02-08
i push send and get:

Error while performing operation.

Could not send message: Broken pipe

---

### Post by finer recliner on 2007-02-08
whats the outgoing mail server (SMTP)? (see account options/prefrences)

it should be something like 'smtp.gmail.com' (this will work to send via your gmail account)

if you're not sure what your outgoing server is supposed to be, let us know what email account you're trying to use, or who your ISP is. most ISP's offer their customers an  smtp server to use.

---

### Post by rgp-02 on 2007-02-08
email acct is hotmail.com (microsoft)
isp is optonline

the main prob right now is :

HOW to get it to set up again

or 

HOW to reconfigure present settings

---

### Post by rgp-02 on 2007-02-08
or................................................

un-install and re-install?

anybody no how to do dat?

---

### Post by benuski on 2007-02-08
Someone correct me if I'm wrong, but you could delete the .evolution folder from your home folder, by going into that folder, hitting <crtl>+<h>, and then moving that to the trash.  That should delete all your setting and allow you to go through setup again.

---

### Post by rgp-02 on 2007-02-08
evolution email not working. i believe i screwed up the setup and want to start over, but i don't know how to start the setup over.............

perhaps un-install and re-install but i can't figure out how to do that either

 any suggestions?

---

### Post by ghandi69_ on 2007-02-08
well.. to remove and reinstall you would just

sudo apt-get remove mozilla-evolution

then sudo apt-get install mozilla-evolution

however... you usually can just go to preferences or options in one of the menus and edit any of the properites to any of the accounts you have set-up.

---

### Post by rgp-02 on 2007-02-08
thanx ghandi 

i did what you said but no success. i still get:

Error while performing operation.

Could not send message: Broken pipe

when i push send

---

### Post by rgp-02 on 2007-02-08
thanx ghandi

i did what you said, but it keeps coming back w/same settings

is there any way to actually DELETE it before re-install?

---

### Post by rgp-02 on 2007-02-08
Hello!..........anybody Alive Out There?

C'mon Now...........let's Wake Up!

Surely A Simple Problem Like This One Won't Stump You, Would It?

There Has To Be At Least One Of You Computer Geniuses..............who Know Everything...............to Crack This One!

I Don”t Have All Day............if You Know What I Mean!

I Would Really Like To Get This Crap Working!

So..............i Wish One Of You Einsteins Would Blow Your Horn On This!

---

### Post by Mr Nick on 2007-02-08
Open up your mail program, click on edit, then preference, and a window will open up. then click edit...which is on the right hand side of the window, and make the changes you want to.

You can also Delete the account by clicking on the remove button as opposed to the edit button (located on the right side of the window.)

---

### Post by rgp-02 on 2007-02-08
Thank you Mr Nick

I owe you a beer!

Problem Solved!

---

