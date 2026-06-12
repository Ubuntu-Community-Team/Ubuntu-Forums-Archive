---
title: "[SOLVED] My Ubuntu was stolen from me! D:"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by SkyPioneer on 2008-03-17
Hey all!
Just a word of warning, this is a hacking related thread. Please do not flame me, this is a serious problem and it needs a soloution.
Moderators and Administrators, I beg of you not to remove the thread until I get an answer.

Thanks, now with that out of the way...


Last night, I let my mother use my computer. When I typed in the password, she wasn't having any of it. She asked for it so she could log in whenever she liked. So I wrote it out for her. Hey, you can trust your mom right? :( I gave it to her, and she didn't like it because it was a combo of letters and numbers and she asked if she could change it to something simpler. I told her it doesn't work and I tried to change the password in front of her but it gave me an infinite loading time.

The next day, I try to log on to linux and :( the password is changed! She will not tell me, she wants to control my internet/computer using habits, and I'm too old for that now! I'm 27, I'm in university and I can't wait for my mother to log me in every time! Besides, what if I need to apply an update?

Well I am writing this from Windows XP (which I have securely passworded now) and I beg of you people for an answer

This is Ubuntu Linux v 7.10 Gutsy Gibbon with all the new updates and all that jazz.
At any rate, I installed it from the live CD which i burnt onto a DVD disc from an iso I downloaded.

So is there any way I can change the password? There is only one account (root account) on the system. I will be willing to download any tools etc/

I need urgent help, Windows XP sucks :(

Thanks in advance

SkyPioneer


PS: My windows XP does not detect the HDD Ubuntu is installed in because the XP hard drive is a slave to the Ubuntu one. Thanks!

---

### Post by Joeb454 on 2008-03-17
Well for a start there shouldn't be just a root account on the computer...

But you could boot into recovery mode (it takes you to a terminal as root), and then add a new user from there, and copy your /home contents from the old user to the new user :)

---

### Post by SkyPioneer on 2008-03-17
I like your style :D
....One problem
I have absoloutly no idea on how to do that :(

---

### Post by sisco311 on 2008-03-17
Reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the command:

```
ls /home
```This command will print the home folders.(home folder name = user name)

Type:

```
passwd username
```to change your password.

```
reboot
```to reboot the computer.

EDIT other commands:
create new (normal)user:

```
sudo adduser username
```

add user to administrator group:
```
sudo usermod -a -G admin username
```

copy files:
```
cp /home/oldusername /home/newusername
```

change the owner of the files:
```
chown -R newusername:newusername /home/newusername
```

---

### Post by stalkingwolf on 2008-03-17
try having a look at this.
[https://help.ubuntu.com/community/LostPassword]("https://help.ubuntu.com/community/LostPassword")

---

### Post by IsawSp4rks on 2008-03-17
Check this thread out for the answer:-

[http://ubuntuforums.org/showthread.php?t=705845&highlight=change+password](http://ubuntuforums.org/showthread.php?t=705845&highlight=change+password)

EDIT : Oops too slow.

---

### Post by SkyPioneer on 2008-03-17
Wow you guys are so great!
Such fast replies, and usefull ones too! I like this forum :D
You guys have my day

---

### Post by Joeb454 on 2008-03-17
Wow...I just realised how complicated my method was :p

---

### Post by mjwhitfield on 2008-03-17
Ok I've stopped lollering.

Joeb's advice is good, boot into recovery mode and make a new user, give them sudo rights and then log in as them and copy your stuff across.  Your mother isn't gonna know how to check how many accounts there are on the system.  Just let her think she's won and use the other account.

On a side note, I suggest spending most of your free time sabotaging her life as much as you can.  Being a bad person is great, you'll enjoy it a lot.

---

### Post by NightwishFan on 2008-03-17
The infinite loading time normally means the password is not able to used. Too short perhaps.

---

### Post by Boyohazard on 2008-03-17
If you can access Grub then it may be possible to change the password otherwise try linux rescue from the installation disk. Oh and give your mother her own account :)

---

### Post by SkyPioneer on 2008-03-17
Hmm, it was a bit short....
Thanks again/
PS: It isn't funny, my mom is evil :D Joking of course.

---

### Post by LeAstrale on 2008-03-17
this should teach you not to share an account with anyone.. one account per user. the fewer admins the better :) remember that me boi :P

Good luck with haunting her!
/Astral-1

---

### Post by NightwishFan on 2008-03-17
I agree. Off topic please forgive me. Where can I find the Mithrandir wizard Tux pic. :)

Never share user even if you trust.

---

### Post by DrMega on 2008-03-17
> **astral-1 said:**
> this should teach you not to share an account with anyone.. one account per user. the fewer admins the better :) remember that me boi :P

Good luck with haunting her!
/Astral-1

Better still, buy her her own computer or get your own place.

---

### Post by Sef on 2008-03-17
I would set your mom up as a user with nonadmin priviledges.  System > Administration > Users and Groups

---

### Post by Joeb454 on 2008-03-17
Can I just ask - why would your mom need to use your computer? Is it actually because she wants to control how much you use it, or because she wants to use it herself?

---

### Post by eragon100 on 2008-03-17
Put a passowrd on your computer's base boot process, (before linux or windows boots) and tell your man you will only allow here to turn on the pc, if she allows you change youir password and give her an nod-administrator one. alternatively, just reinstal ubuntu as if you wanted a dual-boot (resize partition x and use freed space), copy your files from your home folder in the old install to your home folder in the new one (which has a secure password ofcourse) and delete the entire previous installation. All you would have to do if you choose the latter is reinstal some programs :popcorn:

---

### Post by scramasax on 2008-03-17
> **SkyPioneer said:**
> There is only one account (root account) on the system. I will be willing to download any tools

I think you mean it's an *administrative* account.  That's what you get with the default install.

On an admin account you can *elevate* your privileges to root by typing [COLOR="Lime"]sudo[/COLOR] with a command.  But an admin account is not the root account.  Nevertheless, it's more privileges than you need to be running with most of the time.

Mac OS X is the same, and so is Vista.  All the OS vendors expect people to run with more privileges than they need, because they don't want to bother users with understanding the concepts and give them extra things to do.

My suggestion: when you get back control of this machine, set up a non-admin account and use that for day-to-day use.  Or -- easier (since you already have email accounts, bookmarks and stuff) -- set up a new admin account, then log into it and then use that account to take admin privileges away from your original account.

Even if you don't do that for yourself, when a family member says, "May I use your machine?" you can say, "Yes," but you should only offer use of a non-admin account.  If you expect such a request, set one up in advance.  Since Ubuntu, by default, doesn't show users in the login window a bossy relative won't even know what accounts you've got on there.  Just say, "Sure, you can use it; the account name is [COLOR="lime"]skywalker[/COLOR] (or whatever)".  And make sure to take away admin privileges from [COLOR="lime"]skywalker[/COLOR] **before** you offer use of it.  You just go into "users and Groups", get the properties on that user and untick the appropriate box/boxes for what you want people to do/not be able to do on your machine.

---

### Post by billgoldberg on 2008-03-17
I had no idea that it's so easy to change the password.

I assume that you can disable the ls /home  passwd username command? (for companies).

ps: It might be time to think about getting your own place.

---

### Post by mjwhitfield on 2008-03-17
> **billgoldberg said:**
> I had no idea that it's so easy to change the password.If you can physically get to a box, you can do anything.  The only secure PC is one locked away in a room.

Be careful who you trust to use your machine.

---

### Post by kleo skywalker on 2008-03-17
Like people have already said, set up an account *with* administrative privileges only for yourself - so you can install things and update your system. Do not share this account with anyone, and do not give out the password to anyone (even your mother!) Set up another account *without* administrative privileges for your mother (you can set what all she can do while creating the account, and anytime later too - so you can make sure she can use the internet and print stuff and all that, but not install things or snoop into your account). You can also change the file permissions for your /home folder (or the folders in it) so that she can't access your stuff.
Good luck.

---

### Post by Joeb454 on 2008-03-17
If you wanted to be mean, you could always hit Ctrl+Alt+F1 when she wants to use the PC, I bet she'd get really confused...unless she's some sort of *nix guru :lol:

---

### Post by stchman on 2008-03-17
> **SkyPioneer said:**
> Hey all!
Just a word of warning, this is a hacking related thread. Please do not flame me, this is a serious problem and it needs a soloution.
Moderators and Administrators, I beg of you not to remove the thread until I get an answer.

Thanks, now with that out of the way...


Last night, I let my mother use my computer. When I typed in the password, she wasn't having any of it. She asked for it so she could log in whenever she liked. So I wrote it out for her. Hey, you can trust your mom right? :( I gave it to her, and she didn't like it because it was a combo of letters and numbers and she asked if she could change it to something simpler. I told her it doesn't work and I tried to change the password in front of her but it gave me an infinite loading time.

The next day, I try to log on to linux and :( the password is changed! She will not tell me, she wants to control my internet/computer using habits, and I'm too old for that now! I'm 27, I'm in university and I can't wait for my mother to log me in every time! Besides, what if I need to apply an update?

Well I am writing this from Windows XP (which I have securely passworded now) and I beg of you people for an answer

This is Ubuntu Linux v 7.10 Gutsy Gibbon with all the new updates and all that jazz.
At any rate, I installed it from the live CD which i burnt onto a DVD disc from an iso I downloaded.

So is there any way I can change the password? There is only one account (root account) on the system. I will be willing to download any tools etc/

I need urgent help, Windows XP sucks :(

Thanks in advance

SkyPioneer


PS: My windows XP does not detect the HDD Ubuntu is installed in because the XP hard drive is a slave to the Ubuntu one. Thanks!

If you don't have the root password then there is not a whole lot you can do.

You should have made your mom her own account.  This is easily done in the users under administration.  If she won't give you the password then you are forced to reinstall.  You could tell her that you will no longer help her with computer related problems unless she gives you the password.

Also you are surfing the net and logging in as root????!!!!!!!  NEVER log in as root.  It is never needed.

---

### Post by bodhi.zazen on 2008-03-17
Actually, you need to restrict physical access, otherwise there is nothing preventing your mother or anyone else from locking you out.

At 27, perhaps it is time for one to consider living away from home. If you live at home, out of courtesy and respect, you will fall under your mothers rules.

---

### Post by Bölvaður on 2008-03-17
> **bodhi.zazen said:**
> At 27, perhaps it is time for one to consider living away from home. If you live at home, out of courtesy and respect, you will fall under your mothers rules.


How often does this need to be said in one thread to this guy?

I mean, he's a university student, probably very close to getting the degree he has been aiming for and probably already is flirting with job interviewers.

So I'd give him a break... but perhaps I am just nice... and other people isn't...

---

### Post by Terry S on 2008-03-17
Any one thought this guy may be trying to hack into some other persons computer.....just a thought.

---

### Post by NightwishFan on 2008-03-17
If he is lying it won't hurt me. If he is honest then I am glad to be of help. :)

(My password for user and sudo is different both are over 20 chars.)

---

### Post by scramasax on 2008-03-17
> **Terry S said:**
> Any one thought this guy may be trying to hack into some other persons computer.....just a thought.

I guess it's possible, but everything posted in the thread is only knowledge of how the system works, which is available elsewhere, anyway, and shouldn't (and in any case can't) be hidden.  Knowledge of how the system works has to be available: that would hold true even if the source code of the OS wasn't open.  It's the basis on which all users reading this -- which doesn't only include the OP -- must base their decisions on.

---

### Post by Terry S on 2008-03-17
Does that mean that any Ubuntu installation is open to inspection and/or modification by anyone with the code listed earlier i.e. add user etc?

If so the chap who said the only safe computer is one locked in a room on it's own is spot on.

Terry S

---

### Post by bruce89 on 2008-03-17
> **Terry S said:**
> Does that mean that any Ubuntu installation is open to inspection and/or modification by anyone with the code listed earlier i.e. add user etc?

Any old plonker could boot into recovery mode and wreak havoc as they get root access.

---

### Post by scramasax on 2008-03-17
> **Terry S said:**
> Does that mean that any Ubuntu installation is open to inspection and/or modification by anyone with the code listed earlier i.e. add user etc?

If so the chap who said the only safe computer is one locked in a room on it's own is spot on.

If anyone has physical access to any machine all bets are off.  You could run a live Knoppix CD on a Windows machine and get access to files -- because you're running off the CD and bypassing the system's security.

You can't guarantee *absolute* security.

But under normal circumstances it should be sufficient, as has been said, to make sure people who use your machine don't use it under an Administrative account.  It's the same for all platforms.

Oh, and if you don't want your Documents directory to be casually read by other users on the machine set its permissions to rwx (700)

---

### Post by forrestcupp on 2008-03-17
> **sisco311 said:**
> 
```
passwd username
```to change your password.


Wow!  If you can do that, what in the world is the good of having a password?  Anyone can just boot to recovery mode and set it to whatever they want, log in, and do whatever they want with your computer.

It seems like it would be a lot smarter to set it up to where you have to enter the old password before they will allow you to change it to something new.

---

### Post by The Cog on 2008-03-17
Once again - anyone with physical access to the machine has effective ownership. If recovery mode weren't there, there are other ways to take the machine. Physical access is the key. I'm just surprised that people could think otherwise.

---

### Post by bruce89 on 2008-03-17
Ssh, if we stop posting in this thread, no-one will hear of this "flaw".

---

### Post by scramasax on 2008-03-17
> **forrestcupp said:**
> Wow!  If you can do that, what in the world is the good of having a password?  Anyone can just boot to recovery mode and set it to whatever they want, log in, and do whatever they want with your computer.

It seems like it would be a lot smarter to set it up to where you have to enter the old password before they will allow you to change it to something new.

You can protect a Mac from being booted into single user mode.

[http://docs.info.apple.com/article.html?artnum=106482](http://docs.info.apple.com/article.html?artnum=106482)

You set a firmware password.  (there's none set by default.)  The point is that EFI supports that.  I doubt an old-fashioned BIOS would let you.  I suspect we're talking about the firmware here not the operating system as such.

But really, most people's problem is keeping the kids from doing silly things and suchlike not thwarting the NSA.

---

### Post by forrestcupp on 2008-03-17
> **scramasax said:**
> 
But really, most people's problem is keeping the kids from doing silly things and suchlike not thwarting the NSA.

Well, I'm not one of those paranoid people.  I just think it's funny that an OS that boasts of superior security makes it so easy to change a password.  I know someone could break into a computer even without the recovery mode.  But that's just too easy.

Seriously, they should at least make you enter the old password before allowing you to change it.  Every other account I have on the internet at least makes you do that.  It's just logical.

---

### Post by bodhi.zazen on 2008-03-17
> **forrestcupp said:**
> Well, I'm not one of those paranoid people.  I just think it's funny that an OS that boasts of superior security makes it so easy to change a password.  I know someone could break into a computer even without the recovery mode.  But that's just too easy.

Seriously, they should at least make you enter the old password before allowing you to change it.  Every other account I have on the internet at least makes you do that.  It's just logical.

I think there may be some confusion.

If you are a user (not root access) you can not change a password without entering the old password.

If you have root access, you can change a user password without knowing the origional password. This is like resetting a forgotten password.

If you have root access, and no root password is set, you can set one without entering a password (beyond becoming root).

If you have root access, and a root password is set, you will have to enter the old root password before it can be reset.

If you have physical access you can pretty much do what you want. The only "modern" protection you have is to encrypt the file system. This only protects the data / file system if the system is powered down or the (as you have to enter a password to access the crypt). If the system is powered on, encryption offers no protection (talking about encrypting the file system here, not individual data directories / files).

You can of course encrypt data or directories if you want to protect data.

---

### Post by Wicca on 2008-03-17
> **forrestcupp said:**
> Anyone can just boot to recovery mode and set it to whatever they want, log in, and do whatever they want with your computer.

The key is to prevent users from booting into recovery mode. You can:

A) Set a password on the GRUB menu.
B) Remove recovery mode (and memtest) completely from the grub menu, and set the timeout to 0 seconds.
Both A & B: Put a password on the BIOS change the boot order to boot from HDD first.

I did the B trick on some public internet PC's with Ubuntu installed. The only downside is, in case you need to go in recovery mode yourself, you have to reverse the settings:

Go in BIOS, let CDrom boot first.
Put in a recovery CD.
Uncomment the recovery mode line in your menu.lst.
Reboot.

---

### Post by dasunst3r on 2008-03-17
I would boot into recovery mode and issue the command *passwd {username}* (replace {username} with what your user name is and change the password that way.

---

### Post by anjilslaire on 2008-03-17
try this thread for locking down the Recovery mode and grub
[http://ubuntuforums.org/showthread.php?t=192218]("http://ubuntuforums.org/showthread.php?t=192218")

---

### Post by bodhi.zazen on 2008-03-17
> **Wicca said:**
> The only downside is, in case you need to go in recovery mode yourself, you have to reverse the settings:

No you don't.

Boot -> at the grub menu type e to edit, go to the kernel line, add "single" without quotes to the end.

Then hit "enter" to return to the grub screen and then type b to boot.

---

### Post by handydan918 on 2008-03-17
> **forrestcupp said:**
> Wow!  If you can do that, what in the world is the good of having a password?  Anyone can just boot to recovery mode and set it to whatever they want, log in, and do whatever they want with your computer.

It seems like it would be a lot smarter to set it up to where you have to enter the old password before they will allow you to change it to something new.

To address your last point, this can be done by selecting the encryption option at install time. If so set up, the system will require a password before booting.
The whole point of single user (rescue) mode is to allow root access to the system by an administrator with local access. 
Say your one and only Linux guy gets ticked, and walks off the job, never to be seen or heard from again. Instead of suffering through the downtime and other related expenses of reinstalling, you can hire a new admin, and he can fix it. 
The bottom line is this:
there is no such thing as security without physical security. If I can put my hands on your box, it's mine, given a few minutes undisturbed.
Period.

---

### Post by stchman on 2008-03-17
It would appear that it is really easy to add a user:

[http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/](http://www.howtogeek.com/howto/ubuntu/add-a-user-on-ubuntu-server/)

---

### Post by kleo skywalker on 2008-03-18
1) It is neither nice nor anyone's place to tell the original poster that they should move out or any such. If you can help them with their problem, your kindness will be appreciated. If you can't, you're not compelled to post.
2) I really doubt that their mom knows how to do all the stuff that's being discussed as security concerns! She needed help changing the password, so she probably won't be able to break into a computer even if she does have physical access to it.

---

### Post by Wicca on 2008-03-18
> **bodhi.zazen said:**
> No you don't.

Boot -> at the grub menu type e to edit, go to the kernel line, add "single" without quotes to the end.

Then hit "enter" to return to the grub screen and then type b to boot.

Yes I have to.

There's no grub menu visible since I set the timeout to 0 seconds, thus there's no moment to succesfully press an e.

---

### Post by The Cog on 2008-03-18
> **Wicca said:**
> Yes I have to.

There's no grub menu visible since I set the timeout to 0 seconds, thus there's no moment to succesfully press an e.

You can anticipate GRUB and hit the keyboard early (I think escape or up/down arrow will work, less sure about other keys). As long as the key is in the keyboard buffer when grub loads, it will react to it.

---

### Post by Wicca on 2008-03-19
> **The Cog said:**
> You can anticipate GRUB and hit the keyboard early (I think escape or up/down arrow will work, less sure about other keys). As long as the key is in the keyboard buffer when grub loads, it will react to it.

Well I tested it many times and  'cause your post made me uncertain, I tested it again, but Grub does not respond to any keypress. Not pressed on forehand, nor while 'grub should be there', eather pressed constantly or just pressed ones: not on the machines I have.

The only thing I did was removing all the entries in menu.lst except the one neccesary for booting, and set 'timeout  0 '.

You can also set the hiddenmenu flag in menu.lst, in that case grub is not visible but does respond to keypresses as you said, perhaps you confuse it with that.

---

