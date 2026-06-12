---
title: "can't dual boot or format a G4 (lost OSX password)"
date: 2008-06-02
forum: Apple Hardware Users
---

### Post by ruialexbarbosa on 2008-06-02
Hi,

I'm planning to dual-boot OSX and Ubuntu (or would it be best to use Ubuntu + MOL?) I want to use photoshop and lightroom.

I lost my admin password in the OSX 10.4, and I don't have any more users. I mean, I can go into the system, but can't make big changes.

I have OSX 10.3 disks, but if I put them in and press C, the CD starts, but after the apple appears, it moves a bit to the right and everything halts. If I try to install it from the OSX, it asks me the password... I'm basically sruck with this lost password 10.4

Any ideas?

Thanks

---

### Post by oswaldkelso on 2008-06-02
If memory serves me right you can reset the password with the install disks. I think it is possible that the password is locked down but 95% of the time you can just enter a new password using the disks.

---

### Post by aysiu on 2008-06-02
You can reset the password even without the install disks.

When you boot up, hold down Cmd-S to boot into single-user mode. This will bring you to a fullscreen terminal as root.

Type ```
/sbin/fsck -y
/sbin/mount -uw /
``` Then ```
cd /Users
ls
``` to find out the username and ```
passwd *username*
``` to change the password. Then ```
exit
``` to return to the graphical OS X.

---

### Post by ruialexbarbosa on 2008-06-03
[QUOTE to find out the username and ```
passwd *username*
``` to change the password. Then ```
exit
``` to return to the graphical OS X.[/QUOTE]

Ok, but how do I actually CHANGE the password, or reset? Because I get a user named CHLOESANFORD, I put PASSWD CHLOESANFORD and it assumes it, but how can I change it?

Oh, and I'm not talking about login password, but admin password, the one that will let you make changes.

Thanks

---

### Post by aysiu on 2008-06-03
I don't understand what you mean by *assumes it*. Can you explain what exactly happens?

```
passwd chloesanford
``` should *change* the password for the account *chloesanford*. Make sure to type it in lowercase (not uppercase, as you have in the above post).

And you have to run those two other commands first before you can change the password: ```
/sbin/fsck -y
/sbin/mount -uw /
```

Is chloesanford the administrator account? Which one has administrative privileges? Whichever one does, change that account's password.

---

### Post by SouthernPott on 2008-06-06
I am working through the same issues with a Mini I got this past weekend from a garage sale.  Sorry but I am not well versed with command line usage.  Mostly good at following directions.  Hopefully.

Turn on the Mini while holding down the Command + s keys.

Where it says "localhost:/ root #" I typed in "/sbin/fsck -y"

Now I see:
** /dev/rdisk0s3
** Root file system
** Checking HFS Plus volume.
fsck_hfs: Volume is journaled. No checking performed.
fsck_hfs: Use the -f option to force checking.
localhost:/ root#

Now I type in "/sbin/mount/ -uw /

localhost:/ root# cd /Users
localhost:/Users root# ls

and I get to 

.DS_Store  .localized   Robin  Shared  weatherly
localhost:/Users root#  passwd Robin

Here is where I am not understanding.  When I hit return I get
localhost:/Users root#

Do I type in a new password here?  I don't know which of these accounts is the admin account.  On the log in User screen I showed three users, Weatherly, Robin, and Other.  Other had a blank name box and blank password box.

---

### Post by aysiu on 2008-06-06
Sorry, you're doing everything right. I left out the -f option in the first command: ```
/sbin/fsck -**f**y
``` Then run the mount and passwd commands when it's done.

---

### Post by SouthernPott on 2008-06-06
Thank you.  I am afraid that I still don't understand.  I got the code right for the first line

localhost:/ root# /sbin/fsck -fy

and it went through several checks then I put in

localhost:/ root# /sbin/mount -uw /

then

localhost:/ root# cd /Users

then

localhost:/Users root# ls

At this point I get the names of the accounts so then my next line is:

localhost:/Users root# passwd robin 

and it returns 

localhost:/Users root#

This is a G4 Mac Mini and I have no idea which version of OS X it is.  Are they that different?

I guess I am expecting to see some kind of line that says "Enter New Password and Press Return" or something like that.

---

### Post by aysiu on 2008-06-06
That all looks good. I don't know why it's not working. Based on your earlier post, *Robin* is supposed to be capitalized, I think, but that should give you an error message about the username not existing if that's the case.

I did some research, and some versions of Mac OS X require you to run ```
Systemstarter
``` before running the ```
passwd robin
``` command. Can you try that?

---

### Post by SouthernPott on 2008-06-06
after the list of names I tried

localhost:/Users root# Systemstarter and it returned

localhost:/Users root#

I tried passwd Robin and passwd robin and it returned 

localhost:/Users root#

Then I tried systemstarter with a small s and got

localhost:/Users root# Mar 1 06:04:42 systemstarter[50]: Could not create IPC bootstrap port: com.apple.Systemstarter

It did not return the localhost:/Users root# so I typed in passwd Robin at the cursor and it just returned

localhost:/Users root#

---

### Post by aysiu on 2008-06-06
I'm at a loss.

I've done this on my wife's Macbook Pro, and it works. She's running Leopard, though.

Can someone else chime in?

---

### Post by SouthernPott on 2008-06-06
No problem and again, thank you for the responses.  You have left me with information I needed so I have somewhere to go forward from here.  My guess, from what you are saying, is that it is possible for me to get through this without having to buy new Apple software. 

I was hoping that it would be a no brainer like when I put Ubuntu on a couple of PCs for the first time last year.  

The only other info I can offer is that I wasn't the one that purchased this at the garage sale so I didn't get to speak to the people first hand.  The monitor that came with this had two notes.  One said:

Mini Mac - Does Not Boot
         15" LCD & keyboard

Log On: user/password
        root/password

---

### Post by cyberdork33 on 2008-06-06
at the root prompt, type 'passwd' by itself it should let you set the root password, then when you boot to the login screen, choose other, put in 'root' as the user and the password that you created.

Using the passwd command should indeed prompt you to type a password. Maybe it is a security feature.... I will do a test and come back.

EDIT: seemed to work just fine for me

---

### Post by SouthernPott on 2008-06-06
Going through the original steps I am down to the list again.  After the user list I get:

localhost:/Users root#

I type in passwd so it now reads:

localhost:/Users root# passwd  

Press return key and get:

localhost:/Users root#

---

### Post by cyberdork33 on 2008-06-07
> **SouthernPott said:**
> Going through the original steps I am down to the list again.  After the user list I get:

localhost:/Users root#

I type in passwd so it now reads:

localhost:/Users root# passwd  

Press return key and get:

localhost:/Users root#
 
IDK what to tell you. If you have the root filesystem mounted as described above and the passwd command is not working, then I don't know what the issue might be...

---

### Post by SouthernPott on 2008-06-07
Part of what is throwing me on this whole thing is what good is it to have a password protection system if it can be bypassed without an original Apple disk?  Even a copied disk would allow easy access to it from what I read on Apple's website.  They suggested using software close to the same version as the current installation when needing to reset passwords and you have lost your disk. 

Granted I am trying to get into one without benefit of the original disk or anything similar. 

Just got your message while I was typing this up.  Thank you for all the help also.  I have made a correct Ubuntu 8.04 PPC version disk and run it in the Mini once so if all else fails I will just install it and not worry about the Apple side.  It will give me enough new issues to worry about.  I will keep trying to find info on it for now and if I find some success with it I will post back.
  
Best regards.

---

### Post by cyberdork33 on 2008-06-07
any system can easily be taken down if you have physical access.

 I hope you will not give up on OSX entirely. It really is a good OS (but Ubuntu is really good to :) ) You can check ebay for old restores discs. They usually go much cheaper.

---

### Post by SouthernPott on 2008-06-07
I got it this time.  Thanks for all the directions and sorry for the frustrations.  Couldn't have done it without you guys.

Start computer with Command + s

This time my first command was:

localhost:/root# sh /etc/rc

and I got back localhost:/ root#

Typed in /sbin/fsck -fy so I now have:

localhost:/ root# /sbin/fsck -fy 

hit return and I got back localhost:/ root#

Type in /sbin/mount -uw / so I now have:

localhost: /sbin/mount -uw /

hit return and I got back localhost:/ root#

Type in cd /Users so I now have:

localhost:/ root# cd /Users

Hit return and I get:

localhost:/Users root#

Type in ls for:

localhost:/Users root# ls 

Hit return and I get the users list and beneath it:

localhost:/Users root#

Now I type in passwd so it reads:

localhost:/Users root# passwd

Hit return and Voila it asks me to type in a password.

I type it in but it does not give me any prompts or **** that I am getting anything in.  I used my name to make it easy.

Hit return and it asked me to reenter the password.  Typed it in again and it gave me:

localhost:/Users root#

Typed in exit for:

localhost:/Users root# exit 

Hit return.  

The computer restarted and I let it go to the User screen.

Selected Other,  typed in root for the user name and malcolm for the password.

I am in.

Again many thanks.  Hopefully my steps above are close to correct in case anyone references them.  I am going to play with it for a bit before I decide whether or not to keep the Apple side.

---

### Post by cyberdork33 on 2008-06-07
> **SouthernPott said:**
> Again many thanks.  Hopefully my steps above are close to correct in case anyone references them.  I am going to play with it for a bit before I decide whether or not to keep the Apple side.

Good Job!

It is odd that you have to run the rc script manually first.

If you decide to keep it, you should change your root password to something more secure. The root user has ultimate permissions on the system.

---

### Post by SouthernPott on 2008-06-07
I just don't know enough to comment on why those steps worked.  Have had a little bit of time to go over it now and I can see why people like Apple so much.  I went through the updates last night and it was OS X 10.4.7.  Now it is 10.4.11.  Maybe that version required the extra script or maybe I was screwing something up and finally got it right despite the rc scriptt.  

Will change the passwords and user accounts in the next few days.  I just needed something convenient for the time being.  When I first got it I was afraid I would only have the option of putting Linux on it.

Really doesn't look like the people that owned it used it for much more than a handful a school papers and some photo storage.

---

### Post by stream303 on 2008-06-07
> **ruialexbarbosa said:**
> I have OSX 10.3 disks, but if I put them in and press C, the CD starts, but after the apple appears, it moves a bit to the right and everything halts. If I try to install it from the OSX, it asks me the password... I'm basically sruck with this lost password 10.4

One thing to remember is that you can't "downgrade" an OSX installation with a version that it didn't originally come with afaik.  That is, if the system originally shipped with OSX 10.4, it will refuse to install anything less than 10.4 for example.

I'm not sure if this applies to various point-releases though within the same release, ie refusing to install 10.4.2 if it originally came with 10.4.8

Luckily we can install Ubuntu Warty if we really wanted to. :)

---

### Post by cyberdork33 on 2008-06-07
> **SouthernPott said:**
> Really doesn't look like the people that owned it used it for much more than a handful a school papers and some photo storage.
Maybe you can burn a CD with their files and take it back to them :)

---

