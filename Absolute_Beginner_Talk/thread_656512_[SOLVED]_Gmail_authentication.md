---
title: "[SOLVED] Gmail authentication"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by muddler on 2008-01-02
I have used gmail for a many months, without any problems.
A few days ago, I got a "pop up" that reads:
Authentication Required
You must longin to access (my user name)
@ google.com:443/New mail feed
Password: ______________

I have never had a gmail account using my Ubuntu username.
I have no problem getting my mail BUT it is a nuisance that pops up  repeatedly.

Can someone please tell me how to get rid of this.

Thanks:confused:](*,)

---

### Post by meborc on 2008-01-02
what program do you use to check your mail? what is giving those pop-ups...

---

### Post by muddler on 2008-01-03
I use "mail.google.com"

---

### Post by lamalex on 2008-01-03
Can you post a screenshot?

---

### Post by rfruth on 2008-01-03
The gmail cookie expires every two weeks so gotta log back in, is that what you mean ?

[http://mail.google.com/support/bin/answer.py?answer=8494&topic=13260]("http://mail.google.com/support/bin/answer.py?answer=8494&topic=13260")

---

### Post by muddler on 2008-01-03
For more detail:

I use Ubuntu 7.10
Firefox for browser
I hope that helps. I appreciate all the help I can get.

---

### Post by lamalex on 2008-01-03
SS please? It almost sounds like you've been hijacked, I've been using gmail for ever with Ubuntu, and have never gotten a popup to log in.

---

### Post by muddler on 2008-01-03
Sorry, I have no idea how to post a screen shot. Will a detailed description do?

---

### Post by WNxCryptic on 2008-01-03
To place a screenshot, hit the "Print Screen" button on your keyboard, then go into a graphics program and hit ctrl + v to paste the screen shot...save it, and upload it to some place on the web.

---

### Post by Kzin on 2008-01-03
> **muddler said:**
> Sorry, I have no idea how to post a screen shot. Will a detailed description do?

Screen shot works best, however... I hate to pull the classic IT helpdesk on you, but can you please clear your cookies and your cache, Close firefox completely (including your download history) start it back up and try mail.google.com again.  This worked for the people at my company.

This should solve your problem.

---

### Post by muddler on 2008-01-03
I am so new to ubuntu that I don't understand the instructions on how to post screen shots.
The message is about logging on to "pl@google.com:443/New mail feed"
I have never had an email account pl.

---

### Post by The Cog on 2008-01-03
Press PrintScreen to take a screen shot. A Window pops up asking where to save the file. I suggest your desktop. 
In the Ubuntu posting thingy click Go Advanced and click the paperclip to attach the picture to your post.

---

### Post by muddler on 2008-01-03
I followed the instructions. Closed everything except saved passwords. Closed Firefox. When I opened Firefox again, the same popup appeared even before I went to Gmail.
This really doesn't seem to be related to Gmail except in name only. It continues to popup no matter what I'm doing. It's frustrating. I appreciate all the suggestion. I may end up changing the email provider.

---

### Post by seventhc on 2008-01-03
The Prt SC will print your screenshot. upper right hand corner. On my laptop it is the 3rd key from the top most right key.

---

### Post by Iowan on 2008-01-03
I'm nowhere near my Ubuntu/Firefox compute (so I can't get specifics), but you might check the email settings in Firefox - it kinda sounds like Firefox(itself) is trying to check email for pl@gmail...


:oops: Uh... after checking Firefox, I see no email - guess it must have been my OTHER Ubuntu computer which has Firefox/Evolution.

---

### Post by muddler on 2008-01-04
I think you can see screen shot here:

[http://picasaweb.google.com/egerdine/10ChestnutInteriorsAug07/photo?authkey=q0Iwo4bmDmE#5151395336302316898](http://picasaweb.google.com/egerdine/10ChestnutInteriorsAug07/photo?authkey=q0Iwo4bmDmE#5151395336302316898)

---

### Post by muddler on 2008-01-04
Thanks to all for you help. I think I may have it at last.

[ATTACH]55268[/ATTACH]

---

### Post by seventhc on 2008-01-04
It looks like you have it checked off to forget password immediately, now I'm no rocket scientist or linux guru, but I think I would change that to remember password. :P

---

### Post by muddler on 2008-01-04
I've tried checking all three options with no results

---

### Post by seventhc on 2008-01-04
can I ask why you are going through port 443?Gmail doesnt use port 443 Also are you using POP or IMAP???

---

### Post by torgrot on 2008-01-04
I don't think he is trying to get there through pop or imap.  I think he is just going to the web page for google mail.  Did someone else use your computer to check their mail on google at some time?  They may have inadvertenly set the firefox home page to their mail page at gmail.

torgrot

---

### Post by seventhc on 2008-01-04
but the log in in the pic shows a pop up log in box, gmail doesn't use a pop up windows does it??..hmmm is this pop up from the web mail?? I sort of was assuming it was evolution or thunderbird. 
i shouldn't assume.
But from the screenshot, it looks as if thunderbird tar.gz is being opened with 'Archive Manager' so I am not so sure this screen shot is a good representation oh what steps are being taken to log on.

---

### Post by muddler on 2008-01-05
Port 443 was not my idea. That's the way it reads.
I'm using pop.

---

### Post by muddler on 2008-01-05
I have no problem getting my email.I have no problem surfing the web. It's just that the blamed popup arrives each time I click my mouse. Where it originates, I have no idea. I have posted on google forum. Perhaps someone there can come up with an answer. I'll let you know if I get the answer. I sure don't want to have to reinstall.

I appreciate all the help and interest in this puzzle:confused:

---

### Post by rich.bradshaw on 2008-01-05
Port 433 is used for https or ssl.

Starting again, what's the minimum steps needed to get this box?

I think it's to do with using Thunderbird to check email. It's not spyware or anything.

How are you using Thunderbird to check gmail? I'd use Imap rather than anything complex. Check gmails help on how to set it up.

---

### Post by seventhc on 2008-01-05
well, if port 443 is for https i would think it would pop up for a password.
standard pop settings in gmail are
pop.gmail.com  port 995 set to ssl
smtp.gmail.com port 587 set to tls
make your settings match that and it should work fine.

here is a helpful link
[http://mail.google.com/support/bin/answer.py?answer=38343](http://mail.google.com/support/bin/answer.py?answer=38343)

---

### Post by muddler on 2008-01-05
I don't have to take any steps to get the popup box. It come when I am surfing the web! It seems totally unrelated to any program I use. For example: No mail program is running. While writing this post, the popup raised its ugly head.
I tried setting up a gmail account as suggested changing the ports. I still get the same popup. Nothing seems to affect it. BTW I can continue whatever I am doing with the popup on the screen--if I can move around it as it obscures part of the screen.](*,)]

---

### Post by rkd on 2008-01-05
He said his gmail account is NOT pl, which is what the pop-up is asking about.

In Thunderbird, go to the Tools menu, select Accounts Settings, and see how many accounts you have listed there. Is [email]pl@mail.google.com[/email] listed there? If so, that is the source of the problem.  If you delete that account, the popup will go away. You probably ought to figure out how that account got added, though, so it doesn't happen again.

---

### Post by seventhc on 2008-01-05
also gmail won't allow any account with that little bit of letters, I think for gmail 6 is the minimum, if you email that account you will most likely get a failure notice.
But good eye rkd, I never even noticed that it wasn't his email. ](*,)

---

### Post by muddler on 2008-01-07
I never had an email account [email]pl@mail.gmail.com[/email].
After the popup problem started, I did set one up but it had no effect. I got "Invalid address." That account was immediately removed.:lolflag:

---

### Post by Kzin on 2008-01-07
> **muddler said:**
> I never had an email account [email]pl@mail.gmail.com[/email].
After the popup problem started, I did set one up but it had no effect. I got "Invalid address." That account was immediately removed.:lolflag:

Do you have any firefox addons installed? (Tools->Add-Ons)  If so which ones?
What is your firefox start page?
What accounts do you have in Thunderbird?

We'll get to the bottom of this, you wont need a reinstall ;-)  Its just finding the spot where the darned thing is hiding. It's obviously firefox or thunderbird (thunderbird has some tie ins to firefox)

---

### Post by Kzin on 2008-01-07
P.S. I am now pretty sure that this is caused by a RSS feed or an incorrectly configured add-on that checks your mailbox.

---

### Post by rkd on 2008-01-07
If Kzin's suggestion above doesn't lead you directly to the problem, here is something else to try to help learn what is going on: Add a new userid to your system (from the System menu, choose Administration, then Users and Groups).

When you've done that, reboot and login only as the new user and use the system a bit to see whether that popup appears. If it does not appear, then we know it is triggered by something in your normal user account's profile.

---

### Post by muddler on 2008-01-08
To answer Kzin's questions:
[U]
Firefox Add-ons[/U]
Answers, Forecastfox, ubufox, and United States English Dictionary

_Start page_
[www.google.com](www.google.com)

_Thunderbird Accts_
Home and Work

I will try rkd's suggestion and let you know the results. I hope you guys realize how much I appreciate the time and effort you are putting in for my benefit. I'm constantly amazed by the community spirit ubuntu displays

---

### Post by tigerplug on 2008-01-08
Sorry to but in here guys but anyway now of a Gmail checker for Ubuntu that actually works?

---

### Post by muddler on 2008-01-08
rkd hit the jackpot.

The new account does not bring up the popup!:)
When I went back to my usual log in, it returned. What do I do? Delete my usual log in and use another ID? What is the best course to follow?

---

### Post by rkd on 2008-01-08
What the experiment showed is that it is something in the files in your original user profile that is making some piece of software try to check for mail. If you were just to delete and recreate your original user, but keep all the files, the problem probably would still be there. If you are willing to start with an empty account, then that probably is the quickest way to get rid of the popups. 

You would go to System -> Administration -> Users and Groups, select the user, click the Delete button. Then find the user's home directory under /home and delete it (need to use sudo to get privilege to delete other user's files). Then in Users and Groups, click the Add button to create the user again.

If you don't want to wipe out all your files, we would have to spend some more time looking through your files for a clue to what setting is requesting that check for mail. Once we learn which setting is causing the popup, it probably would be very quick to fix the problem.

So, which path do you want to take? The quick fresh start, or the long search for the setting that is causing the popup?

---

### Post by muddler on 2008-01-08
Can I save my bookmarks and add them to the new accoun?. Fortunately I do not have a lot of important stuff worth saving.

However, being an inquisitive sole, I'm going to play around and see if I can find the cause of the problem. BTW to keep from going even more stark raving mad, I moved the popup to another workplace where it sat angrily glaring at me.

Thanks to everyone who offered help.

---

### Post by muddler on 2008-01-08
While "playing around" I ran across something that *may* help. When I clicked on Mail Notification under system>preferences, the screen reads, under Mailbox List, "pl @gmail.com" Below it states no mailbox selected. There are several buttons but none respond. Do you have a suggestion as how to remove that as the remove button is greyed out?:confused:

---

### Post by rkd on 2008-01-08
Saving your bookmarks and restoring them to the recreated account should be safe.

I don't have a Mail Notification in my System -> Preferences, so I can't look to see what it is like.  I can make a guess that if you click on the email address to highlight it, that might make the Remove button become active.

If that lets you remove it and if removing it makes the popup stop, good. If not, keep looking around a bit and you might find something else. If you don't find what's causing the popup but still want to investigate, open a Terminal, enter the command:
```
ls -al
``` And paste the output into a post here. The files in your home directory might give clues as to where to look.

---

### Post by muddler on 2008-01-08
The Mail Notification screen is dead. It will not respond to any action. Below is the result of the list you requested. 

pl@park-laptop:~$ ls -al

total 3540

drwxr-xr-x 39 pl   park    4096 2008-01-08 14:59 .

drwxr-xr-x  4 root root    4096 2008-01-08 11:17 ..

-rw-------  1 pl   park     294 2008-01-08 14:12 .bash_history

-rw-r--r--  1 pl   park     220 2007-12-17 06:48 .bash_logout

-rw-r--r--  1 pl   park    2298 2007-12-17 06:48 .bashrc

drwxr-xr-x  3 pl   park    4096 2007-12-17 12:17 .cache

drwxr-xr-x  7 pl   park    4096 2007-12-26 16:10 .config

-rw-rw-r--  1 pl   park  237719 2007-12-19 12:20 cpm.exe

drwx------  2 pl   park    4096 2007-12-19 10:22 .cups

drwxr-xr-x  3 pl   park    4096 2008-01-04 16:29 Desktop

-rw-------  1 pl   park      28 2008-01-08 11:33 .dmrc

drwxr-xr-x  2 pl   park    4096 2007-12-19 15:48 Documents

drwxr-xr-x  3 pl   park    4096 2008-01-04 15:59 Downloads

-rw-------  1 pl   park      16 2007-12-17 12:17 .esd_auth

drwxr-xr-x  8 pl   park    4096 2008-01-08 11:18 .evolution

lrwxrwxrwx  1 pl   park      26 2007-12-17 06:48 Examples -> /usr/share/example-content

drwx------  3 pl   park    4096 2007-12-17 14:42 file:

drwxr-xr-x  2 pl   park    4096 2007-12-29 13:38 .fontconfig

drwx------  6 pl   park    4096 2008-01-08 11:33 .gconf

drwx------  2 pl   park    4096 2008-01-08 15:05 .gconfd

drwxr-xr-x 22 pl   park    4096 2008-01-03 14:22 .gimp-2.4

-rw-r-----  1 pl   park       0 2008-01-08 11:11 .gksu.lock

drwxr-xr-x  5 pl   park    4096 2007-12-27 12:24 .gnome

drwx------ 17 pl   park    4096 2008-01-08 14:59 .gnome2

drwx------  2 pl   park    4096 2007-12-17 12:17 .gnome2_private

drwxr-xr-x  2 pl   park    4096 2007-12-27 16:51 .gstreamer-0.10

-rw-r--r--  1 pl   park     237 2008-01-08 11:33 .gtk-bookmarks

-rw-r--r--  1 pl   park      86 2007-12-17 12:17 .gtkrc-1.2-gnome2

drwxr-x---  2 pl   park    4096 2007-12-26 11:01 .gtodo

-rw-------  1 pl   park     845 2008-01-08 11:33 .ICEauthority

drwxr-xr-x  2 pl   park    4096 2007-12-21 13:57 .icons

drwxr-xr-x  3 pl   park    4096 2007-12-17 12:17 .local

drwx------  3 pl   park    4096 2008-01-04 10:01 .mozilla

drwx------  3 pl   park    4096 2008-01-04 10:01 .mozilla-thunderbird

drwxr-xr-x  2 pl   park    4096 2007-12-17 12:17 Music

-rw-r--r--  1 pl   park 2799336 2007-12-24 16:30 MyFunCardsSetup2.0.4.21.exe

drwxr-xr-x  3 pl   park    4096 2008-01-08 11:18 .nautilus

-rw-r--r--  1 pl   park  307200 2008-01-05 15:44 nautilus-debug-log.txt

drwx------  3 pl   park    4096 2008-01-03 17:53 .openoffice.org2

drwxr-xr-x  2 pl   park    4096 2007-12-17 12:17 Pictures

-rw-r--r--  1 pl   park     566 2007-12-17 06:48 .profile

drwxr-xr-x  2 pl   park    4096 2007-12-17 12:17 Public

-rw-------  1 pl   park    3620 2007-12-31 11:53 .recently-used

-rw-r--r--  1 pl   park   38193 2008-01-08 14:59 .recently-used.xbel

-rw-r--r--  1 pl   park       0 2007-12-17 13:18 .sudo_as_admin_successful

drwxr-xr-x  2 pl   park    4096 2007-12-17 12:17 Templates

drwxr-xr-x  2 pl   park    4096 2007-12-17 13:19 .themes

drwx------  5 pl   park    4096 2007-12-26 11:12 .thumbnails

drwxr-xr-x 13 pl   park    4096 2008-01-04 11:13 thunderbird

drwxr-xr-x  4 pl   park    4096 2007-12-25 09:55 .tomboy

-rw-r--r--  1 pl   park    5385 2007-12-25 09:56 .tomboy.log

drwx------  2 pl   park    4096 2008-01-04 11:15 .Trash

drwxr-xr-x  2 pl   park    4096 2007-12-17 13:18 .update-manager-core

drwx------  2 pl   park    4096 2007-12-17 12:17 .update-notifier

drwxr-xr-x  2 pl   park    4096 2007-12-17 12:17 Videos

drwx------  2 pl   park    4096 2008-01-04 08:52 .w3m

drwxr-xr-x  2 pl   park    4096 2007-12-27 10:52 .wapi

-rw-------  1 pl   park     122 2008-01-08 11:33 .Xauthority

-rw-r--r--  1 pl   park    5502 2008-01-08 14:59 .xsession-errors

pl@park-laptop:~$

---

### Post by rkd on 2008-01-08
The only thing I notice on a quick look at the list of files is that I see .evolution, which is where the Evolution program stores profile information. Evolution is an email client, so it would be logical for it to ask for a password to an email account, but I don't know whether it would start up when you logon without you actively opening Evolution. Evolution does include an appointment calendar and I imagine it pops up reminders when a meeting time is approaching, so it might start up automatically whenever you logon.

So if you haven't already checked this, open Evolution (Applications -> Internet -> Evolution). From the Edit menu, choose Preferences. In Preferences, click on Mail Accounts, and see whether the unwanted account appears there. If it does, you should be able to delete it and be done with the annoyance.

If that isn't the answer, and if you want to keep on looking rather than wiping out and recreating your account, I can think of one more thing to do to try to find out where the popups are coming from:

The next time you boot the computer, first logon as the account that doesn't get the popups. Open a Terminal and enter the following commands:
```
ps -A >ps.none
chgmod 0777 ps.none
```That will write a list of all the programs running into the file ps.none and change its permissions so anyone can read it. Exit the Terminal, logoff, and logon as your normal account.

As soon as you logon as your normal account, open a Terminal and enter the following command:
```
ps -A >ps.first
```
Leave the Terminal open. As soon as a popup appears, go to the Terminal and enter the command:
```
ps -A >ps.second
```
Compare the list of programs to see whether anything that is present in ps.first or ps.second is not in ps.none, and think about what that program does -- could it be expected to try to look at your email, perhaps just to tell you that you have new email to look at?

If you can't spot any obvious culprit in the lists, attach the files to a post (I assume they will be longer than makes sense to paste into a post), and we'll try to find a clue. Remember that when attaching ps.none, you will have to give the path name of the other account.

---

### Post by muddler on 2008-01-08
Thanks to everyone and particularly rkd for your help. I think I have spent enough time on this and I'm sure that you have better things to do with yours. I'll remove this account after copying the bookmarks. Fortunately I've not had it long enough to lose much.:)

---

### Post by macogw on 2008-01-08
> **tigerplug said:**
> Sorry to but in here guys but anyway now of a Gmail checker for Ubuntu that actually works?

Check Gnome Mail aka cgmail...google for it.  Someone on here developed it.

---

### Post by id3379 on 2008-01-08
Is this only on your computer or does this happen on any computer you use ? if its only yours its likely your browser cookies...cache..etc..like some other members said above. Or you could try using Evolution, i havent had one problem with my iMap account :)

---

### Post by muddler on 2008-01-09
With the new suggestions, I'm resuming my search for the source of the problem. I tried the steps suggested by rkd but no list appeared. I probably did something wrong. In the meantime, I've left the offending popup in another workplace, so it's not a problem.
Thanks to all

---

### Post by Kzin on 2008-01-09
Hehe, 
I think you have us all as curious as to what it is as you are!

Lets find out what that Network dealie is.
Right click your menubar
Select Edit menus.
Go to preferences
Find the Mail Notification deal and right click on it
Choose properties
What is the command it is running?

---

### Post by rkd on 2008-01-09
Concerning my suggestion that didn't seem to work for you, did you look into the files ps.none, ps.first, and ps.second using an editor? The output of those ps commands will be put into those files (and not to the screen, which I suppose might have confused you into thinking they didn't work).

---

### Post by muddler on 2008-01-10
Thank you, Kzin and rkd. As an eighty-five year old newbie, I was born before the human race had a gene mutation so that babies today are born knowing how to use a computer. What was it the head of OLPC said? That it takes about four minutes for a child to learn how to use the computer. If you can put up with my lack of basic knowledge, I'll keep plugging away. Remember, I was brought up in tha age of vacuum tubes when few if any ever dreamed of computer chips.
I'll try to follow your suggestions and will let you know the results.:)

---

### Post by muddler on 2008-01-10
I'm not sure this helps but the Command reads: mail-notification--display properties. Under Comments: Configure Mail Notification

---

### Post by Golem XIV on 2008-01-10
May be a stupid question, but when you go to mail.google.com do you have the checkmark on the  "Remember me on this computer" box?

Also check your Firefox settings under Edit -> Preferences, Privacy tab, make sure that the "Always clear my private data when I close Firefox" is NOT checked (enabled).

<Edit> DOH!  Sorry, I just saw the first page, didn't realize there were more...

---

### Post by muddler on 2008-01-10
You probably didn't realize how uninformed I am as to linux and ubuntu. Now, by using the text editor, I can show the lists. You state that when attaching the files, I will need to give a path. Sorry, but how do I do that?

---

### Post by Kzin on 2008-01-10
> **muddler said:**
> I'm not sure this helps but the Command reads: mail-notification--display properties. Under Comments: Configure Mail Notification

Beautiful.
Based on your research I was able to find the program that is responsible for these notifications...
[Gutsy Package]("http://packages.ubuntu.com/gutsy/gnome/mail-notification")
[Original Author's Webpage]("http://www.nongnu.org/mailnotify/")

The "quick" way to get rid of this is to run the following command
```
sudo apt-get remove mail-notification
```
in the terminal (how to get to the terminal is covered previously in this thread)

Now that is the quick way, not sure about the right way because we don't cover exactly what installed this application.  You could be losing functionality somewhere else that you don't expect to lose.  That being said, I have a fresh Gutsy install here and do not have that application, nor do others here in this thread.  So I think you should be ok to remove it.

If you opt not to remove the application outright, the Author's website implies that you should not only be able to configure the application to suppress the display pop-ups, but be able to remove the gmail account alltogether.  I do not have it installed so I wont be able to guide you through that if it is what you wish to do.

Hope this helps!

---

### Post by Kzin on 2008-01-11
> **muddler said:**
> ...As an eighty-five year old newbie...

For an 85 year old newbie you seem to be adapting very quickly. :KS:KS:KS I think it's great that you are delving into the world of linux and am very happy to help. =D

---

### Post by rkd on 2008-01-11
muddler: Now that Kzin has helped you identify what is causing the popup, we probably don't need the ps.xxxx files, but don't delete them until you are sure the popups are gone. If we still need to look at them later, I'll give you clearer directions then about how to attach them to a post and what a path is.

It seems that the mail-notification package got installed either directly by you (unlikely) or as an unexpected result of something you did install. Do you remember installing something shortly before the popups started appearing? If so, what was it (or them, if you installed more than one thing recently).  Kzin rightly points out that if you remove the mail-notification package, there is a small chance that would upset something that you do want. So it would be good to figure out what brought mail-notification into your computer.

There probably is some way to ask the package management software what other packages depend on mail-notification, but I don't know how to do it.

But it probably won't cause any harm to just remove it, as Kzin shows, and just watch for side-effects.  If when you run the command Kzin gives you, it tells you something about other things that depend on mail-notification, pay close attention to the message. If you aren't sure what it is telling you, copy it down and tell us what it says (or use the mouse to copy the messages from the terminal and past them into a post here) and we will explain it to you and we can figure out how it affects you.

If you would rather not remove mail-notification, but try to make it stop the popups,  but can't figure out how to tell it to stop, I have a test system on which I could install the package and learn enough about it to tell you how to make it stop. Just ask if you'd prefer to try that solution.

Kzin: Good tip - I didn't know about that approach. Thanks for pointing it out.

---

### Post by muddler on 2008-01-11
I'm willing to take a chance. I long ago learned that I benefit more from my mistakes than from my successes. If I lose something, I can track it down and reinstall it.

I have already run into a problem. When I go to Terminal and do the mail notification removal,I get the next line 
[sudo] Password
When I enter my password, nothng happens. It does not enter. What else should I do?

---

### Post by seventhc on 2008-01-11
You won't see the password or any characters as you type it so it will appear as if you aren't typing anything. Just type it in anyway and press enter. It is being entered it's just that it doesn't show any output. It's a security thing. :)

---

### Post by muddler on 2008-01-11
Here we go again! I followed the directions for removing mail notification. It was successfully removed. The final line was "Do you want to continue? Yes  No

Is there more to be done here?

---

### Post by rkd on 2008-01-11
I assume it was asking whether you wanted to continue with the removal, and I hope you answered Yes.

Assuming that is true, I think you need to use the computer a little to see whether the popups are gone.  It might not be necessary, but I suggest shutting down and restarting the computer, just to make sure there isn't anything left over from before, then use the computer enough to know whether the popups have stopped.  If they have stopped, we can declare the problem solved. If they have not stopped, we have some more work to do.

So please let us know whether the popups are gone or not.

---

### Post by muddler on 2008-01-11
Hallelujah and the Saints be praised, not to mention the helpful and caring members of the Ubuntu Community.

I removed the mail notifier and rebooted. It has been plenty long but no unwanted popup!:) The help is greatly appreciated but the confidence I got from all those who chipped in to help solve the problem was the greater benefit. Knowing that competent help is just a click away is reassuring. It has been a great learning experience for me.
THANKS

---

### Post by Zylar on 2008-01-11
Wow, kudos to all involved here, especially muddler.  I only hope I'll be in good enough condition to learn a new os when I'm 85...

This just reinforces why I always tend to come to this community for help, gj all.

---

### Post by Kzin on 2008-01-11
> **rkd said:**
> I assume it was asking whether you wanted to continue with the removal, and I hope you answered Yes.
Indeed, answering No would not uninstall the package.  If you are worried about what it is uninstalling, feel free to paste the output in a reply and we'd be happy to give our input.

Edit: Ignore this post as I forgot to submit it, by the time I did it was no longer relevant.

---

### Post by Kzin on 2008-01-11
> **muddler said:**
> Hallelujah and the Saints be praised, not to mention the helpful and caring members of the Ubuntu Community.

I removed the mail notifier and rebooted. It has been plenty long but no unwanted popup!:) The help is greatly appreciated but the confidence I got from all those who chipped in to help solve the problem was the greater benefit. Knowing that competent help is just a click away is reassuring. It has been a great learning experience for me.
THANKS

You are quite welcome =)

---

### Post by rkd on 2008-01-11
I'm glad to hear that you've got it solved, muddler.

Now we don't need those files ps.first, ps.second, and ps.none that we created a while ago.  They are small and it won't hurt anything if you leave them on the computer, but if you want to clean up, it is pretty easy to delete them.  To get rid of the first two, open a Terminal and enter the commands:
```
rm ps.first
rm ps.second
```
To get rid of the other one, login as that test account you created, open a Terminal, and enter the command:
```
rm ps.none
```
Now I hope you enjoy using Ubuntu. And if you have a question or problem, someone will be here in the forum to help.

---

