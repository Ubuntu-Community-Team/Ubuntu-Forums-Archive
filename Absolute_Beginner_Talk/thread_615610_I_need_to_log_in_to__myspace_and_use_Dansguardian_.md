---
title: "I need to log in to  myspace and use Dansguardian at the same time."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by marianlibrarian on 2007-11-17
[SIZE=4]**[COLOR=Blue]Advice for Ubuntu 6.06 Dapper Drake systems.[/COLOR]**[/SIZE]

I have a unique problem. Yes, I have searched through this forum and found nothing related. I have yet to figure out what Dansguardian is using as a forum. I just need help.

I sent a message to myspace first and here is what transpired:

> [SIZE=4][COLOR=Purple]**My Problem**[/COLOR][/SIZE]
**[FONT=Arial][SIZE=2][FONT=Arial][B]Body :**[/FONT][/SIZE][/FONT][/B]
  [FONT=Arial][SIZE=2][FONT=Arial]10/30/2007 01:54 PM CONTACT REQUEST FORM SUBMITTED 
---- 
Subject: Account - Other 
Body: 

I am the library director of a small rural library that allows my patrons to access myspace. I also have a profile for our library: myspace/genevapubliclibrary 

The problem has occurred before. We are using Ubuntu 6.06 Dapper Drake with Dansguardian filter set to medium. I mention Dansguardian because I can log in from an Ubuntu 6.06 computer that is not using Dansquardian.  

What happens? When a user logs in, it shows their name, "Hi, Person's Name" but it does not take them to their home page, and when the user clicks on the Home link it refreshes the start page and says above the "Hi, Person's Name" with a message in red that says, "You Must Be Logged In To Do That". 

I am one of a few public libraries that allow patrons to access myspace. I hope you can help me. 

Thank you for your attention to this matter. 

Marian Librarian 

**[SIZE=4][COLOR=Purple]Their replay....[/COLOR][/SIZE]**

[/FONT][/SIZE][/FONT][FONT=Arial][SIZE=2][FONT=Arial]Hello,[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]Thank you for contacting Customer Support at MySpace.com[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]If you cannot log in to your MySpace profile, please try again now. [/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]If you are still experiencing difficulties, please provide us with the following information and restate your issue to help us further assist you. If you are a band profile, you are required to submit a salute and send your request to [EMAIL="musicsupport@myspace.com"]musicsupport@myspace.com[/EMAIL][/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]            Current Email/Log in Address:[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]            New Email/Log in Address:[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=Arial]            - If necessary[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]            MySpace Password or Salute (required for identification):[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=Arial]            -  If you wish to change your password, you will need to provide a salute – a salute is a current photo of yourself holding a handwritten         [/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]               sign containing your friend id (located in the web address bar after “friendid=”.)[/FONT][/SIZE][/FONT]
  
  
  [FONT=Arial][SIZE=2][FONT=Arial]A link to your site (friend ID or URL) would also be very helpful as there may be an error with your email/log on address.[/FONT][/SIZE][/FONT]
  
  
  [FONT=Arial][SIZE=2][FONT=Arial]PLEASE "REPLY" TO THIS EMAIL WITH THE APPROPRIATE INFORMATION.[/FONT][/SIZE][/FONT]
  
  [FONT=Arial][SIZE=2][FONT=Arial]For the most up to date messages about MySpace, subscribe to the MySpace Help blog! You get updates almost every day! Go here to subscribe.[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=Arial][www.myspace.com/myspacehelp]("http://www.myspace.com/myspacehelp")[/FONT][/SIZE][/FONT]
  
  
  [FONT=Arial][SIZE=2][FONT=Arial]Thank you,[/FONT][/SIZE][/FONT]
  [FONT=Arial][SIZE=2][FONT=Arial]MySpace.com[/FONT][/SIZE][/FONT]
I have been struggling with this for several months. I want my patrons to be able to access their myspace accounts. Can someone help me??

And please, All my computers are using **[SIZE=6][COLOR=Red]Ubuntu 6.06 Dapper Drake[/COLOR][/SIZE]**. 
Please Please only instructions for Dapper Drake. I say this because I tried to install Adobe Reader on a machine and had advice for every Ubuntu version imaginable and it still doesn't work.

Thanks - Marian Librarin

---

### Post by Kingsley on 2007-11-17
I did a quick Google search and figured out that Dansguardian has blacklist files. Maybe your problem could be solved through editing them. Check out this directory ```
/etc/dansguardian/lists/blacklists
```

---

### Post by marianlibrarian on 2007-11-17
I looked in that place and myspace wasn't listed - I don't think it was. Anyway, if it were listed there it would simply direct the patron to that warning screen telling them they tried to access a forbidden site.

This is something different. I was able to narrow it down to Dansguardian. I have my filters set to medium. I set them to low and still same problem. I turned it off and you can log into myspace and get to the home page and check messages as normal. But when I turn Dansguardian back on - the problem is back. It accesses myspace.com. It allows you to log in as it SHows you your name right there BUT when you try to go to your home page ----- it says "your name" and still says that you must be logged in to do that.

This is something that happened a few months ago. Maybe some update/upgrade from DAnsguardian? I don't know. It is a nasty headache for me right now as I would also like to access my library's myspace account from work.

---

### Post by por100pre1 on 2007-11-17
There are many parents concerned about their children visiting the "MySpace" web page. I'm pretty much sure DansGuardian will try to enforce MySpace blocking as much as possible. Look for a circumventor web proxy server. BTW, I think you should try another service, e.g. [Google]("http://pages.google.com/").

---

### Post by marianlibrarian on 2007-11-17
I see.

Your assistance to this matter has been greatly appreciated.

---

### Post by stock99 on 2007-11-18
anyway, have you tried to add [myspace.com](myspace.com) into the /etc/dansguardian/exceptionsitelist  ?


ok, i try to use the setting for youngest children (50, instead of 100) in the file  /etc/dansguardian/dansguardianf1.conf
and i add the myspace.com into the exceptionsitelist file. I can login to my page  and go into inbox and go chat (but i have no friend coz i just create the account for testing. ).


remmeber to do /etc/init.d/dansguardian restart     
else it will still remember the old setting. Normally, 'reload' is enough, but 'restart' just to make sure :P

---

### Post by ktraglin on 2007-12-17
myspace.com is found in:

/etc/dansguardian/blacklists/kidstimewasting/domains
/etc/dansguardian/blacklists/chat/domains

however, since policies change, i would go for adding myspace.com to /etc/dansguardian/exceptionsitelist.  that way, it's very easy to remove it if you should ever need to.

---

### Post by Michael_TSM on 2008-01-30
I found I could login to Myspace with DansGuardian active if I logged in through this page:
[login.myspace.com/index.cfm?fuseaction=login.process]("login.myspace.com/index.cfm?fuseaction=login.process")
Which is the page that normally comes up when you type in the wrong username or password, but you can get to it straight away by using that link.

EDIT: *cough* This work around works fine!

---

