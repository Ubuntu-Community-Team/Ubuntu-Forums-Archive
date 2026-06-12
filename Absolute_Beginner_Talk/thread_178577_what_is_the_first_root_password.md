---
title: "what is the first root password?"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by argoscitrus on 2006-05-17
I finished to install Ubuntu 5.10 normally but never ask for root password. What is the first password? why the program didn't askme during instalation? how can i solve ?

---

### Post by Buffalo Soldier on 2006-05-17
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Please refer to that link.

---

### Post by aysiu on 2006-05-17
Read this, too:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by glotz on 2006-05-18
I think that argoscitrus here raises a valid point, not everybody knows that Ubuntu doesn't have a root account (by default). Actually most people are pretty clueless about this fact. I think this should be emphasized during the install. I remember being baffled by this myself. A room for improvement in Dapper methinks.

---

### Post by zerhacke on 2006-05-18
I was going to post here about how you can reenable the root account, but there's no real need to.  Sudo does everything you will need root to do, and it's safer.

If I see some really good reasoning on why you need root and sudo isn't acceptable, I'll tell you how to do it, but frankly I don't forsee this happening.

---

### Post by gr0kzer0 on 2006-05-18
"Re-enabling" root is hardly a biggie. Just open console and type```
sudo passwd root
``` and you can set a password of your choice for root.

I agree that sudo is sufficient.  Since I gave my root account a pw I don't think I've used it once.  But this whole issue does need to be made prominent during install or somewhere.  This question crops up again and again.

---

### Post by aysiu on 2006-05-18
[QUOTE=glotz]I think that argoscitrus here raises a valid point, not everybody knows that Ubuntu doesn't have a root account (by default). Actually most people are pretty clueless about this fact. I think this should be emphasized during the install. I remember being baffled by this myself. A room for improvement in Dapper methinks.[/QUOTE] Why do they need to know unless they're Linux users? Ask most Windows users--they don't know what "root" is.

Of course, they usually run Windows as administrator anyway, so they'll be in culture shock regardless (unless they go with Linspire's default settings).

If they click on Add/Remove Applications, they'll be prompted for their password. If they click on Login Screen Setup, they'll be prompted for their password. It's the same thing as Mac OS X. It's the *exact* same thing. Apple doesn't feel the need to explain this. Why should Ubuntu?

---

### Post by glotz on 2006-05-18
Why should Ubuntu? Because Ubuntu should be the best OS in the universe, or at least strive to be the one! ;)

---

### Post by macdo on 2006-05-18
Why should Ubuntu be geared **exclusively** towards Windows migrants?

When I first installed Ubuntu, I came from Debian...

---

### Post by joshrobinson on 2006-05-18
is enabling the root password so bad? i hate typing sudo in front of all of my commands, so i login as root in the terminal with su

it just makes it less typing in the terminal for me

---

### Post by aysiu on 2006-05-18
[QUOTE=macdo]Why should Ubuntu be geared **exclusively** towards Windows migrants?

When I first installed Ubuntu, I came from Debian...[/QUOTE] But people coming from Debian or other distributions are most likely to be the ones who complain about not being able to log in as root.

"Why can't I log in as root?" --people coming from other Linux distros
"Why can't I change any files?" --people coming from Windows

---

### Post by xtacocorex on 2006-05-18
[QUOTE=joshrobinson]i hate typing sudo in front of all of my commands, so i login as root in the terminal with su
[/QUOTE]

You can still mimic a root terminal with sudo flags, sudo -s or sudo -i.

I'm sorta glad that we use sudo because it's saved my a** a couple of times.

---

### Post by RudolfMDLT on 2006-05-18
[QUOTE=aysiu]But people coming from Debian or other distributions are most likely to be the ones who complain about not being able to log in as root.

"Why can't I log in as root?" --people coming from other Linux distros
"Why can't I change any files?" --people coming from Windows[/QUOTE]

You are 100% correct! I used Red Hat for about 3 weeks last year(got intimidated) gave up and this time I'm giving ubuntu a try! Things are going great!

When I tried to copy my mp3's from a DVD to HDD I couldn't because I was informed I had no rights to do so. The file system is Ext 3. Maybe I configured it wrongly? -Any help or comments welcome and apreciated-

Anyway, comming from windows  i thought - "Why can't I change any files?"
and being a linux novice - "Why can't I log in as root"!

So i'm going to enable root so as to gain acces to my Hard Drive. If anybody can tell me possibly what I did wrong as to the setting up of my drive making it inaccessible I would apreciate it!

I partioned 50GB into 3 partitions, root(Ext 3), swap(Swap) and data(Ext 3).
data is the one that only root can access.

---

### Post by aysiu on 2006-05-18
[QUOTE=RudolfMDLT]I partioned 50GB into 3 partitions, root(Ext 3), swap(Swap) and data(Ext 3).
data is the one that only root can access.[/QUOTE] Assuming your data partition is mounted at a folder called /data, these would be the commands you would paste into the terminal: ```
sudo chown -R rudolf:rudolf /data
sudo chmod -R 755 /data
```

---

### Post by joshrobinson on 2006-05-18
[QUOTE=RudolfMDLT]You are 100% correct! I used Red Hat for about 3 weeks last year(got intimidated) gave up and this time I'm giving ubuntu a try! Things are going great!

When I tried to copy my mp3's from a DVD to HDD I couldn't because I was informed I had no rights to do so. The file system is Ext 3. Maybe I configured it wrongly? -Any help or comments welcome and apreciated-

Anyway, comming from windows  i thought - "Why can't I change any files?"
and being a linux novice - "Why can't I log in as root"!

So i'm going to enable root so as to gain acces to my Hard Drive. If anybody can tell me possibly what I did wrong as to the setting up of my drive making it inaccessible I would apreciate it!

I partioned 50GB into 3 partitions, root(Ext 3), swap(Swap) and data(Ext 3).
data is the one that only root can access.[/QUOTE]

what is the mount point for your data parition?
.... looks like i got beat to it

---

### Post by gr0kzer0 on 2006-05-18
Aysiu, there are users coming from Windows, from other Linux distros, from Apple, from nothing.  When I started, I had a little Windows experience.  I read about Unix and Linux, and Ubuntu was the first distro I tried.  Luckily, I'd read about the root situation in Ubuntu, otherwise I would have been one of those newbies wondering why I can't log in as root.

I think the root situation is unusual for Linux and therefore needs pointing out.  Hell, search this forum and see how many people have asked about it. And then tell me it doesn't need explaining.

---

### Post by user1397 on 2006-05-18
[quote=xtacocorex]You can still mimic a root terminal with sudo flags, sudo -s or sudo -i.

I'm sorta glad that we use sudo because it's saved my a** a couple of times.[/quote]
how exactly has it saved your a**?
how would it be different then logging in as root?
---just wondering, not criticising---

---

### Post by glotz on 2006-05-18
[QUOTE=macdo]Why should Ubuntu be geared **exclusively** towards Windows migrants?[/QUOTE]

Ubuntu is the only OS that I know that "doesn't have root". (And besides that, I think it makes a lot of sense to acknowledge that windows does have a special position in some things.) There are a lot of windoze users out there and they're the ones who need to be saved! :)

---

### Post by macdo on 2006-05-18
I do agree that Windows users are most certainly the vast majority of all new users. But that wasn't quite my point. 
What I meant was that while Windows users are used to having all the rights all the time (which is a Bad Thing), Linux users know that they'll need to be root to do certain things. They are obviously surprised not to see their usual installation step, especially because it is one that they are used to taking particular care with.
A quick sentence on the Create User screen of the installer, for example, would not have gone amiss. 

Ubuntu prioritises Windows users by just creating a user account. The fact that the account in question does not have administrative rights is beside the point, as far as they're concerned - they know their password, and type it in when a box presents itself (and that is most definitely a Good Thing). It's also a good thing that people can't (at least when they start using Ubuntu) log in as root.

It would however have been possible to avoid confusion for people arriving from any other Linux distro (except, of course, and sadly, Linspire), and it's a bit of a shame that didn't happen. Nothing serious, mind you - but a pity. 

Of course, these are just my opinions, even if I do tend to pronounce them in a rather assertive tone (that's what being a teacher does to you, unfortunately :-D )

sudo su avoids the repetition of sudo at the command line: helpful if you want to auto-complete commands.

macdo

---

### Post by aysiu on 2006-05-18
[QUOTE=glotz]Ubuntu is the only OS that I know that "doesn't have root".[/QUOTE] You don't know Mac OS X. It's been around a few years. You should take a look. [http://www.apple.com](http://www.apple.com)

---

### Post by JNowka on 2006-05-18
A few words

CTRL + ALT + F1

login

sudo -i

enter password

startx -- :1

Done :)

*edit* oh yeah, don't forget to log out of gnome and root before going back to the main screen using CTRL + ALT + F7

---

### Post by joshrobinson on 2006-05-18
you can let yourself login to gnome as root by going into system administration login window then clicking security tab and "allow system admin login"

so roots not exactally "not there" its just disabled for security

---

### Post by skippy81 on 2006-05-19
I personally like the current status quo.  The less questions you are asked in a standard install the better If you ask me.  If someone is an expierienced Linux user, they can select the "expert setup", but I think windows migrants and first time users would be better off not dealing with root - and indeed not having to read a paragraph about "su, sudo and disabled root" during setup :D

---

### Post by aysiu on 2006-05-19
Well, there seem to be two things at issue here:
[b]
1. Should Ubuntu have the same defaults as other Linux distros (one root, one user)?[/b]

I don't think this is going to change. That's fundamental to how Ubuntu's always been, it's what OS X uses as well, and I think it keeps things the simplest. The pros and cons of this model are well outlined here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

On a personal note, I find it easier to give complete instructions than saying "make sure you're logged in as root by typing *su* and then entering your root password; then paste in these commands."

[b]
2. If Ubuntu continues to default to *sudo*, what should users be told about it?[/b]

Frankly, the only thing I would think makes sense is that if you're in a system folder and you try to modify something that you have a dialogue that pops up to tell you it's a system file and that you need to be an administrator to modify it, and if you are in the *sudoers* file that you then be prompted for a password.

I believe, given what I've seen in Dapper even when you use *gksudo nautilus*, that this is the direction that Ubuntu development is headed, so that we won't have to keep telling new users to create *gksudo nautilus* and *kdesu konqueror* launchers.

---

### Post by RudolfMDLT on 2006-05-20
Firstly: Thank you aysiu! The 
[I]
sudo chown -R rudolf:rudolf /data
sudo chmod -R 755 /data[/I]

 commands did the trick... but it did scare the crap out of me when I saw the condole tearing through my windows XP system(that i probably should have mentioned :) ). I'll be doing some text base command studying this weekend to cure my ignorance. The MS filesytem was NTSF so no damage done. - Thank you very much.

Just a comment on the whole "should root be enabled by default thing"

My first time in GNOME and not having any access to my drive I had a little panic and went right clicking every where, trying to copy random stuff and mucking around in every administrative tool I could... that was stupid. Had I had the "power" of root I would have destroyed the system! &#8211; The graphical (windows like) environment makes mistakes too easy too make for newbies from Windows or Mac OS.

Finding out where root had gone and what to do about it took me 10min at most thanks to this  awesome forum!  Enabling root was 2 lines in a text-base shell... old hat Linux users should have no trouble with that! And the fact that root can't by default login to GNOME is a very good failsafe for anybody thats new to Linux, again, that can be enabled(as joshrobinson pionts out) quit quickly.

I would be nice though if it could mensioned at install.

---

### Post by RudolfMDLT on 2006-05-20
... I double posted a message ](*,) 

I can edit it, but how do I delete it?

---

### Post by steve.horsley on 2006-05-20
[QUOTE=aysiu]
[b]
1. Should Ubuntu have the same defaults as other Linux distros (one root, one user)?[/b]

I don't think this is going to change. That's fundamental to how Ubuntu's always been, it's what OS X uses as well, and I think it keeps things the simplest. The pros and cons of this model are well outlined here: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[/QUOTE]

Actually, the cons haven't been discussed there - only the pros. As I see it, there are two major cons:

1: 
sudo is fragile. 
If you change your hostname, you probably then have to use rescue mode to fix it because sudo won't let you in any more. I've seen several users here in trouble because sudo doesn't like something. Some broken file permissions break sudo too.

2:
sudo asking you for **your** password is insecure
I can walk up to any Ubunto desktop (say theg user went to get a coffee) and gain full control with just two commands:
  passwd
  sudo passwd
Any damn trojan I download and execute can do the same, right in front of me.

So the first thing I do these days is to set a root password, and configure sudo to ask for the root password instead of my own. And reconfigure sshd to disallow rooot logins.

---

### Post by glotz on 2006-05-20
[QUOTE=RudolfMDLT]... I double posted a message ](*,) 

I can edit it, but how do I delete it?[/QUOTE]
You cannot. Only mods can. (A bit strange if you ask me!) :???:

---

### Post by glotz on 2006-05-20
[QUOTE=steve.horsley]
sudo asking you for **your** password is insecure
I can walk up to any Ubunto desktop (say theg user went to get a coffee) and gain full control with just two commands:
  passwd
  sudo passwd
[/QUOTE]
I don't understand how this can get you root. :confused:  Care to explain?

---

### Post by steve.horsley on 2006-05-20
[QUOTE=glotz]I don't understand how this can get you root. :confused:  Care to explain?[/QUOTE]
**passwd** - change the users pasword to one I know
**sudo passwd** - change roots password. I will be asked for the password of the account I'm using (but I know that cos i just changed it) and then asked for the new root password. And now the machine is mine. Bwwa-ha-ha-ha! I can use **su** any time I like, and the shmuck who owns the PC doesn't even know that there **is** a root password.

---

### Post by catlett on 2006-05-20
I don't like the security of the sudo timeout (if that is correct?)
Meaning if you type sudo and your password then for 15 minutes no password is needed. Now you're just like a windows user if the malicious software knows to type sudo or if someone comes to your computer while you stepped away and the 15 minutes are up and they know about sudo.

P.S. I don't know why people are so defensive about making information clear? You sound like a bunch of fascists who think they know what is best for the little people. It is their computer they should know everything about it. Including that sudo is the default method and how to get to the traditional root terminal and how to launch nautilus as root. I don't think people should be condemned to pasting other peoples instructions from a forum. They should be able to figure out the system or learn it. Enough giving a fish for a day, start teaching to fish.

To get a root terminal ```
sudo su
```
To make a root password you know  ```
sudo passwd root
```
To launch nautilus as root so you can graphically change permisions (by right clicking to properties and then clicking on permissions) as well as delete folders etc. that the user doesn't own ```
gksudo nautilus
```

P.S.S. Why assume anything? Why gear towards Windows newcomers or Mac or Freebsd or Solaris or Unix or whatever. Just explain how the system works in it's entirety. Let the person decide what they want to do.

---

### Post by glotz on 2006-05-20
But **passwd** asks for the old password before allowing you to change the current users password. Or am I missing something here? (And if you allready know the old password, then you've got all it take to root...)

---

### Post by catlett on 2006-05-20
If you use sudo passwd root it gives a prompt that says enter new unix password then after enter it asks for you to reenter the password. 
are you trying to create a root password?

---

### Post by glotz on 2006-05-20
[QUOTE=catlett]I don't know why people are so defensive about making information clear? You sound like a bunch of fascists who think they know what is best for the little people.[/QUOTE]

WTF are you talking about?

[QUOTE=catlett]are you trying to create a root password?[/QUOTE]

Nope. Maybe you should read the thread...

---

### Post by Kvark on 2006-05-20
About security. If you walk away from your computer to get a cup of coffee or whatever and someone else sneaks up to it then they can read your personal files and delete everything in your home dir even without messing with passwords.

So **always** select "system -> lock screen" from the menus before leaving the computer. If you ever go to the bathroom without locking the screen when there are others around then it's entirely your own fault if someone does "rm -r /home/you/*" which doesn't require any password.


About the confusion. The gksudo password prompt says "please enter your password..." not "please enter the root password...". So why do people think it wants the root password? :-?

Well, if people are confused it might be good to explain it during the installation but then I think it needs to be explained in a way that everyone understands regardless of which OS they come from. So using the word "root" when explaining sudo would be unacceptable.

---

### Post by glotz on 2006-05-20
I think it's all very simple. There's only 1 password. If you don't know it, you can't even login to the system to begin with, that is, [if you have configured your system a bit](http://ubuntuforums.org/showthread.php?t=177984)... If you know it, then you can do whatever you like. I think that all one user systems should work like this. We don't need root.

---

### Post by catlett on 2006-05-20
[QUOTE=glotz]I think it's all very simple. There's only 1 password. If you don't know it, you can't even login to the system to begin with, that is, [if you have configured your system a bit](http://ubuntuforums.org/showthread.php?t=177984)... If you know it, then you can do whatever you like. I think that all one user systems should work like this. We don't need root.[/QUOTE]
If someone is coming from another linux distro they get confused by sudo. Most distros use su and a root password to get to root.
I think your missing the whole point. It is about security in your system. Restricting the permissions of users so they or malicious software cannot alter the system. If it someone's personal computer and it is only their system this might seem unimportant. But if you are setting up a server or network or multiple users it is very important to control permissions. From a security point of view one universal password that is entered once at start up and gives full access is a disaster. That is why windows has so much trouble with viruses, trojans, etc.
I apologise for talking over your head. Although this is your thread that post was about the subject that arose it was not a response to you. I don't expect you to know what I was saying. My response about fascism isn't as much this thread but about the ongoing response to the sudo su issue and how it has been dealt with by those in charge. Your responses show my point. You can't easily change your password. You should know how to change your password, use su if you choose, etc without hunting for the explanatioin or posting about it. Plus I always think of Linus' "gnome nazis" comment when users aren't given a choice of actions but instead a default is setup without their input.

P.S. I asked which password because people have posted a way to change your root password as well and I couldn't tell by your response where your error was coming from.

---

### Post by aysiu on 2006-05-20
[QUOTE=steve.horsley]Actually, the cons haven't been discussed there - only the pros.[/quote] Before you correct someone, read the link he posts: > Downsides of using sudo

Although for desktops the benefits of using sudo are great, there are possible issues which need to be noted:

    *

      Redirecting the output of commands run with sudo can catch new users out. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents.
    *

      In a lot of office environments the ONLY local user on a system is root. All other users are imported using NSS techniques such as nss-ldap. To setup a workstation, or fix it, in the case of a network failure where nss-ldap is broken, root is required. This tends to leave the system unusable unless cracked. An extra local user, or an enabled root password is needed here. That's straight from the Wiki. > As I see it, there are two major cons:

1: 
sudo is fragile. 
If you change your hostname, you probably then have to use rescue mode to fix it because sudo won't let you in any more. I've seen several users here in trouble because sudo doesn't like something. Some broken file permissions break sudo too. I'll give you that. Plenty of people here have messed up their /etc/sudoers files or /etc/group files and not been able to do anything without rebooting into recovery mode.

> 
2:
sudo asking you for **your** password is insecure
**I can walk up to any Ubunto desktop (say theg user went to get a coffee) and gain full control with just two commands:**
  passwd
  sudo passwd
Any damn trojan I download and execute can do the same, right in front of me.

So the first thing I do these days is to set a root password, and configure sudo to ask for the root password instead of my own. And reconfigure sshd to disallow rooot logins. Anyone who has physical access to your computer has full control of it if she knows what she's doing.

First of all, she can boot into recovery mode. That makes her root already. She doesn't *have* to change your password.

She can boot a Knoppix CD and have access to everything on your computer.

She can take a screwdriver and remove your hard drive.

This doesn't make *sudo* any less secure than *root*. And having a separate *root* password doesn't make you any more secure than having only one password for user and *sudo*... especially if you pick bad passwords.

A security model is only as strong as the user using it. If the user is stupid, it doesn't matter how good the defaults are.

---

### Post by Kvark on 2006-05-20
[QUOTE=aysiu]Anyone who has physical access to your computer has full control of it if she knows what she's doing.[/QUOTE]
If the system is secure then they can't do antyhing without opening the case. For example when I had a laptop in highschool it required a bios password to boot. And I always locked the screen before getting up from the chair even if I wasn't going to leave the room. So my friends wanting to play dirty pranks on me could not unlock it without my user password and could not boot a live cd or recovery mode without my bios password.

The only way they could have done anything to my system would have been to open the laptop and use the bios reset jumper on the motherboard or move my hard disk to another computer. But opening a laptop case and putting it back together is a bit too much work to do while the owner is getting a coke.

---

### Post by aysiu on 2006-05-20
Thanks for the clarification, Kvark. I'm going to assume that your friends would be people you can trust to do no more than a prank (change your wallpaper to something embarrassing).

Anyone with malicious intent would steal the laptop while you were getting a coke, not try to open it then and there.

---

### Post by argie on 2006-05-20
To address the original topic,

I had a little trouble with this, to the extent that I actually reinstalled once thinking that I'd forgotten to enter a root password.

Why not have a screen where the person who's installing can set the root password (during installation), with the option to click a checkbox that says "do not set a root password"
What's the big deal anyway? My Ubuntu doesn't let me login with root at the login screen, but lets me su -

I don't see how that's a security risk.

---

### Post by steve.horsley on 2006-05-21
It seems I have been corected tiwce. 

I clean forgot that changing your own password requires you to re-input the current one. Shows how often I change mine! Actually, that softens my feelings against Ubuntu's sudo approach quite a bit. But there is still only one password to know to own the whole machine, and I am still uncomfortable with that. 

Aysiu - sorry, yes there is a list of two cons. The piping thing has caught me out occasionally, e.g. **sudo lshw > less**, but I don't consider that really major. And I have never used nss-ldap so that's not on my personal radar. As you see in the paragraph above, my biggest gripe, such easy access to root stuff was based on poor memory. But I still think sudo is unsuitably fragile. I have seen posts here from people who got locked out after changing the hostname, changing file permissions, and even just from changing the time. And that fragility is not mentioned.

---

### Post by aysiu on 2006-05-21
[QUOTE=steve.horsley]As you see in the paragraph above, my biggest gripe, such easy access to root stuff was based on poor memory. But I still think sudo is unsuitably fragile. I have seen posts here from people who got locked out after changing the hostname, changing file permissions, and even just from changing the time. And that fragility is not mentioned.[/QUOTE] Maybe you should tack that on in the Wiki entry as a *con*. I'm in total agreement with you there. I've seen that happen a lot here.

---

### Post by peterj on 2006-05-21
The more people using ubuntu the more resources ubuntu has to impove itself.
Who poses a bigger market, other linux os's or windows?

---

