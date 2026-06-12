---
title: "Huge Problem!!!! Help Immediately!!!"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Ubun2User on 2007-12-11
Okay, so I had my Ubuntu account set-up under my name but I have switched to a Mac and gave my wife the Ubuntu machine.

Anyway, I went to change the user info and I also went into some advanced settings and changed the /root folder from root/michael to root/lauren, now when I try to log-in, I get the following error.

Your home directory is "home/lauren" but it does not seem to exist. Do you want to login the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

Please help!!!  If my wife wakes up tomorrow and her computer isn't working, she will kill me!

Thanks!

---

### Post by chips24 on 2007-12-11
reinstall the system and save all the information onto a disk, thats what i would do, it wouldnt take too long

---

### Post by chips24 on 2007-12-11
> **chips24 said:**
> reinstall the system and save all the information onto a disk, thats what i would do

just kidding

---

### Post by Ubun2User on 2007-12-11
Jesus man, don't do that...someone, what do I do so I can go to bed...lol

---

### Post by RedNikon on 2007-12-11
At the command prompt type :
```
cd /home/
ls
```
If there is a directory called "lauren" you good if not hope you have one called "michael"

If you have one called "michael" but not "lauren" type in ```
mkdir /home/lauren
``` log in and -copy- the files over.

---

### Post by Ubun2User on 2007-12-11
I can't get past the login...how do I get to the terminal?

---

### Post by RedNikon on 2007-12-11
When you start up the machine what is the prompt, or what does it say on the screen?

---

### Post by Ubun2User on 2007-12-11
I don't need to change anything  BUT the login screen.  I just needs to have a login for her.

---

### Post by Ubun2User on 2007-12-11
/home/michael file exists

---

### Post by chips24 on 2007-12-11
theres a menu on the bottom left handside of the login screen, the terminal should be there.

---

### Post by NullHead on 2007-12-11
At the login prompt click on sessions and then select gnome or kde failsafe. That will get you a terminal.

---

### Post by Ubun2User on 2007-12-11
okay, I see the failsafe terminal

---

### Post by RedNikon on 2007-12-11
There should be an option to run terminal after click on the session button.

---

### Post by NullHead on 2007-12-11
login with you're user account and use the commands given earlier.

---

### Post by Ubun2User on 2007-12-11
I no longer have an account, I changed the account into to my wifes...

---

### Post by 1337455 10534 on 2007-12-11
Worst comes to worst, let your wife use a LiveCD to get past the day... But making a new folder for 'Lauren' should work.. In Feisty though, I tried changing the root password, among other things, and being the n00b I was I did a clean install...

---

### Post by NullHead on 2007-12-11
double post error ... sorry ....

---

### Post by RedNikon on 2007-12-12
Can you log in under hers?

---

### Post by Ubun2User on 2007-12-12
It does have all admin rights...I just changed the login info for the master account

---

### Post by Ubun2User on 2007-12-12
I know what I did but i can't fix it.

I changed the /home/michael to /home/lauren

---

### Post by RedNikon on 2007-12-12
Then log in under her account, and execute the commands a give earlier.

---

### Post by Ubun2User on 2007-12-12
> **RedNikon said:**
> At the command prompt type :
```
cd /home/
ls
```
If there is a directory called "lauren" you good if not hope you have one called "michael"

If you have one called "michael" but not "lauren" type in ```
mkdir /home/lauren
``` log in and -copy- the files over.

I have one called"michael" and I did this and it says permission denied.

---

### Post by Ubun2User on 2007-12-12
Look , I wish I hadn't changed it from /home/michael to /home/lauren, how can I change it back so I can at least log in?

---

### Post by RedNikon on 2007-12-12
```
sudo mkdir /home/lauren
```

---

### Post by NullHead on 2007-12-12
you need to do ```
sudo mkdir /home/lauren
```

PS: WOOOO 300th post!!!

---

### Post by Ubun2User on 2007-12-12
Ok, did that, now I get this when I try to login...

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions User's $HOME directory must be owned by user and not writable by other users.   then there is an Ok button...press that and get...

Your session only lasted 10 seconds. if you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.  there there is a view details button and an ok...click ok and it takes me back to the login screen

---

### Post by NullHead on 2007-12-12
ok try this ```
sudo adduser lauren
``` and then try to login.

---

### Post by Ubun2User on 2007-12-12
it says lauren already exits

---

### Post by Ubun2User on 2007-12-12
is there anyway to go back to earlier like in windows?  is there a way to revert the change in home directory back to michael?

---

### Post by Leilas Lacis on 2007-12-12
Could you try

[FONT="System"]adduser lauren --home /home/lauren[/FONT]

---

### Post by NullHead on 2007-12-12
I'm not sure .. I would reinstall and copy my files off onto a usb-flash/pen drive.

---

### Post by bettlebrox on 2007-12-12
Boot into failsafe mode and move the michael directory to be called lauren then change the ownership on it to lauren's:

cd /home
mv michael laurne
chown -r lauren:lauren lauren

Make sure your in the /home when you issue the last 2 commands.

---

### Post by RedNikon on 2007-12-12
Let me know if bettlebrox's soultion works.

---

### Post by Ubun2User on 2007-12-12
No it didn't work...it reads...

Invalid option -- r

---

### Post by Ubun2User on 2007-12-12
This is ridiculous...it should not be so easy to change something like this if it causes this much trouble!!!!!

---

### Post by NullHead on 2007-12-12
I'm not sure whay you're having trouble like this. I'm sorry if that damages you're feelings about linux or ubuntu, but please keep in mind for next time that you should make a new user and copy the files .. not what ever you did. 

I would think of it this way. You're learning how NOT to change a profile around.:lolflag:

---

### Post by Ubun2User on 2007-12-12
Funny but if I don't fix this tonight...I won't need Ubuntu...I will need a box to lay in for eternity.

I can't believe there is no way to fix this.  All I did was change the home directories name from michael to lauren...WTF!

---

### Post by Leilas Lacis on 2007-12-12
Have you checked out

[http://ubuntuforums.org/archive/index.php/t-595038.html](http://ubuntuforums.org/archive/index.php/t-595038.html)

---

### Post by natehall on 2007-12-12
You could trace the problem back to the beggining by using the arrow up and down keys while in the terminal. (Everything done in the terminal is logged.)

---

### Post by dhruva023 on 2007-12-12
we should always use the official way for doing official things.

---

### Post by dhruva023 on 2007-12-12
you should just create new accout using adduser.

sudo adduser <username> (that's what i read from above link.)

then copy your wife's file to it.

then delete your wife's accout.  and recreate it with what ever rights you want, and copy back her files into that accout.

it would take more then 10 to 15 minutes

---

### Post by bettlebrox on 2007-12-12
> **Ubun2User said:**
> No it didn't work...it reads...

Invalid option -- r
My mistake, should be -R

---

### Post by CaptainInsaneO on 2007-12-12
I've never seen someone so scared of his wife before... :|

Really hope he got it fixed. [-o<

---

### Post by Ubun2User on 2007-12-12
I didn't get it fixed...lol  I had to re-install the operating system today and lost everything...oh well...lol

She was pissed and we fought a little but all is well now...she is currently using Ubuntu and seems to really like it!  Now we are both happy...living Windoze free.

---

### Post by 1337455 10534 on 2007-12-15
You couldn't salvage anything? A flashdrive and a LiveCD would have sufficed, but I haven't read everything that has been posted on this thread so that probably wasn't a valid option...

Nice Avatar CaptainInsaneO!

---

### Post by jriggz on 2007-12-17
> **chips24 said:**
> just kidding

Why on earth would you do that? Not only is it not funny, but it's just plain... not funny. Jokes like that really aren't appreciated on a support forum.

---

