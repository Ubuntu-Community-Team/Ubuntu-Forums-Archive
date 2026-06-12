---
title: "password protect a file"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by frog3764 on 2007-04-15
Greetings to the Group - This is a repeat as I didn't get any response from a previous thread.  I want to password protect a file.  I tried a code but it worked only once, then not again.  gksudo "gnome-open %u"  I need a step by step as I'm a newbie / dummy. All help is appreciated.

Frog

---

### Post by Seisen on 2007-04-15
Check this link out and see if it helps you with your problem. If you need any help let me know and I will see what I can do to help. I see I forgot my link. You posted the link I forgot to put in.

---

### Post by bodhi.zazen on 2007-04-15
How 'bout if I add a link ?

[http://www.cyberciti.biz/tips/linux-or-unix-password-protecting-files.html](http://www.cyberciti.biz/tips/linux-or-unix-password-protecting-files.html)

---

### Post by frog3764 on 2007-04-15
Hey Seisen Thanks - I should have stated in my post that I want to password a folder. Can I do this too?  What did I do wrong with this command "gnome-open %u"?  It seemed to work one time as I had to enter my password to get in, but it didn't work the next time.  I made a new Launcher and did it that way for the folder. 

Frog

---

### Post by bodhi.zazen on 2007-04-15
Well, first in Linux files are protected by permissions.

So for the folder in question set the permissions to 700

```
chmod 700 /folder
```

Don't leave the computer unattended (log out).

You should be fine.

Permissions: [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

Also I think the command yo want is :

```
gksudo nautilus
```

But you should not need that code if you are not performing sys admin (ie be careful what you do with that).

---

### Post by frog3764 on 2007-04-15
I must be doing something wrong.  I typed in the code in the terminal just like you have it, and I changed the "folder" to the name of my folder.  Is that correct?  Do I need something else before the chmod?  In my post I stated I'm a newbie / dummy!  If I put this in the permissions tab in the folder, then where do I put it?

Thanks

---

### Post by bodhi.zazen on 2007-04-16
I would guess the path is wrong.

chmod 700 /path/to/directory

For example, if the directory is "folder" (without quotes) in your home directory all these will work :

chmod 700 /home/user_name/folder
chmod 700 ~/folder

Note In the first you must change "user_name" to your log in name.
In the second, ~ is short hand for /home/user_name

HTH

---

### Post by steve.horsley on 2007-04-16
To password protect a folder full of files, you could try this HOWTO:
[http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/](http://www.movingtofreedom.org/2007/02/21/howto-encfs-encrypted-file-system-in-ubuntu-and-fedora-gnu-linux/)

---

### Post by frog3764 on 2007-04-17
Hey bodhi.zazen and Steve - thanks for your help.  I looked at Steve's link How To but that's too far beyond me at this point.  The codes you have me are to be put into the terminal, right?  It doesn't work for me there.  I used my "user name" and the name of the folder, but nadda.  What am I doing wrong?

Frog

---

### Post by fakie_flip on 2007-04-21
Try truecrypt or seamonkey.

---

### Post by frog3764 on 2007-04-22
I appreciate all the information here but I can't get anything to work to password protect a folder.  I've read the links and tried the commands, but I need some "step by step" to figure this all out.  I'm a newbie / dummy and need some more help.

Thanks,
Frog

---

### Post by bodhi.zazen on 2007-04-22
> **frog3764 said:**
> I appreciate all the information here but I can't get anything to work to password protect a folder.  I've read the links and tried the commands, but I need some "step by step" to figure this all out.  I'm a newbie / dummy and need some more help.

Thanks,
Frog

First I again encourage you to read about permissions. If you set the permissions on the directory (folder) then only you will have access to the directory.

chmod 700 /folder

With those permissions no one but you (and root) has access to the folder, so where is the problem  ?

To go beyond that you are talking encryption.

And, well, not to be rude, the link steve.horsley gave you is a step-by-step how to.

There is a section titled "HOWTO: EncFS for Ubuntu 6.10 (Edgy Eft)"

So, If I were to write a "how-to" here it would be the same as in that link....

Please, read the link and describe where you are getting stuck or what part you do not understand and we will try to help ...

---

### Post by fakie_flip on 2007-04-23
sudo apt-get install seahorse

then generate some keys. after that you can encrypt files. the files will require a password to decrypt them.

---

### Post by frog3764 on 2007-04-25
Hey bodhi.zazen thanks for the reply.  Now what I don't get is where do I put your code chmod 700 /path/to/directory?  You talk about permissions, so is that where I put it into, or is it the terminal?  I tried the terminal but it didn't work.  The permission sounds like the best as long as I need to enter the password to open up the folder.  That is what I want to do.  As for Steve's "How to link", I will have to study that some more.  There is a lot there I don't understand.

Frog

PS I guess this will all work for 7.04 now as I just updated.

---

### Post by bobbob94 on 2007-04-25
The instructions need to entered in a terminal (Applications>Accessories>Terminal). If you need to encrypt a folder rather than just change the permissions you can install Seahorse from Synaptic Package Manger. Then it will appear in Applications>Accessories>Passwords and Encryption Keys. Start it up, and you create a key (Key>Create New Key>PGP Key) Once you've done this you should have an Encrypt option when you right click on a folder. Click this, then select the key you just made and it will produce an encrypted version of the folder called yourfoldername.zip.pgp, and there you go. You can also use your key to encrypt your email but thats a whole other topic!

---

### Post by bobbob94 on 2007-04-25
When you said the chmod 700 command didn't work what exactly did you mean by the way? When you right click on the folder afterwards, and go to properties>permissions,  do "group" and "others" still have folder access? If not, then it worked...This won't give you password protection though, it just means that when other users are logged on with their account they can't access your files, so maybe you're better off checking out my last post if you need password protection

---

### Post by bodhi.zazen on 2007-04-25
> **frog3764 said:**
> Hey bodhi.zazen thanks for the reply.  Now what I don't get is where do I put your code chmod 700 /path/to/directory?  You talk about permissions, so is that where I put it into, or is it the terminal?  I tried the terminal but it didn't work.  The permission sounds like the best as long as I need to enter the password to open up the folder.  That is what I want to do.  As for Steve's "How to link", I will have to study that some more.  There is a lot there I don't understand.

Frog

PS I guess this will all work for 7.04 now as I just updated.

Well if you want password protection you are talking encryption. Seahorse sounds like your best bet.

FYI, until then, you can have protection with permissions.

Yes, open a terminal, the command you wnat is "chmod" and you need to tell the command which folder you want to protect. Say you have a folder "MyFolder" you want to protect in your home directory. Then the command is :

```
chmod 700 ~/MyFolder
```

~ = short hand for /home/username

If you change the permissions no one except you and the root (administrative) user will have access to the folder (directory). You will be safe as long as you do not leave the computer unattended. Either lock the screen or log out.

Here is a link on permissions : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

---

### Post by leibowitz on 2007-04-25
To all trying to help frog3764 : What he wants is to protect some files (or directory). What many of you did say is to encrypt files. That's not protection, that's encryption.

To frog3764 (and those who talked about permissions): this is the way to go. Just follow bodhi.zazen, he seems to be far more observing than others here.

---

### Post by fakie_flip on 2007-04-25
Encryption is protecting his files, and it does ask for a password. frog3764, install seahorse using Synaptic.

---

### Post by leibowitz on 2007-04-25
He don't want to encrypt the content. Just to make it not readable by other. 

Basic linux permissions does the job. I can start a vote if you want.

---

### Post by ViRMiN on 2007-04-25
Encryption is the way to go!  Anyone can get access to the files using permissions simply by booting with a Live CD...

---

### Post by frog3764 on 2007-04-25
It sure seems like I'm real dumb because I can't figure out most of this, and on top of that, a simple search for Seahorse in the Synaptic Package Manager comes up empty.  Maybe it has a different name listed, but I can't find it.  As for the encryption, that sounds like what I need.  I only want to password protect a folder in my Home folder, or I can place it anywhere for that matter.  Even though I'm the only one using the pc, if someone else would use it, as the pc is on all day, then someone can't open it up.  So, lead me to Seahorse and I'll try that.

Thanks for all your help and understanding.
Frog

---

### Post by bodhi.zazen on 2007-04-25
> **frog3764 said:**
> It sure seems like I'm real dumb because I can't figure out most of this, and on top of that, a simple search for Seahorse in the Synaptic Package Manager comes up empty.  Maybe it has a different name listed, but I can't find it.  As for the encryption, that sounds like what I need.  I only want to password protect a folder in my Home folder, or I can place it anywhere for that matter.  Even though I'm the only one using the pc, if someone else would use it, as the pc is on all day, then someone can't open it up.  So, lead me to Seahorse and I'll try that.

Thanks for all your help and understanding.
Frog

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=seahorse&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=seahorse&searchon=name&subword=1&version=all&release=all)

You need to enable your repositories :

[http://cutlersoftware.com/ubuntuinstall/#enabling_extra_repositories](http://cutlersoftware.com/ubuntuinstall/#enabling_extra_repositories)

---

### Post by neymac on 2007-04-25
You can use file roller:
1.Create a package with the files you want protect
2.With file roller opened, select Edit =>Password and chosse your password.

To extract or view the file, file roller will ask for the password.

---

### Post by frog3764 on 2007-04-25
Thanks to everyone for all their input!  I  GIVE  UP!  I looked at the links and I think I selected the right repository,  but I still didn't find anything that looked like Seahorse.  The "I guess samples" listed on the other link, well, which one should I select?  A dummy Newbie like me doesn't have a clue.

Thanks again, but I give up on this.  I will just bury the folder deep someplace where even I won't be able to find it.  Sorry for all the time wasted on this.

Frog

---

### Post by fakie_flip on 2007-04-26
What files do you want to password protect? If they are open office documents, you can choose to save those files with a password when saving them in Open Office. What part of the instructions from the links do you not understand? Where are you stuck? You should enable the universe and multiverse repositories using Synaptic, then click on the reload button in Synaptic, and seahorse will be there along with a lot of other software you didnt have available before.

---

### Post by frog3764 on 2007-04-26
OK Guys - I've got Seahorse.  I look at the docs and all they talk about is files or email.  I want to protect a folder so that only I can open it.  I don't see that in the Seahorse.  Tell me more about the permissions.  No one here will have any idea anyway of how to get anywhere in the pc anyway.  If I can password or just restrict anyone else from opening a folder, that will do, but the password would be better.  Just like when I try to open up some other files here, I have to put my password in again.  That's what I want to do with this folder.

Frog

---

### Post by harun on 2007-04-26
Install truecrypt-
```
sudo apt-get install truecrypt
```
Create the volume you want, put in what size suits your needs-
```
truecrypt --size 200MB --type normal --encryption AES --hash RIPEMD-160 --filesystem FAT -c myvolume.tc
```
Create a directory where you would like to have the password protected directory-
```
mkdir mysecretdir
```
Mount your truecrypt volume in that directory-
```
truecrypt -u myvolume.tc mysecretdir
```
To dismount that directory-
```
truecrypt -d mysecretdir
```

You will need to mount that directory to access it and provide the password. It is pretty neat because that directory you create, without it mounted you can actually put files in it. Then when you mount it providing the password you see all your hidden files. So no one accessing your computer would ever know it was there, they would see the other files.

(These commands taken from [http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/](http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/) to suit your needs)

For all the people answering this request with "chmod" explanations, what is wrong with you? When someone asks how to PASSWORD PROTECT A FILE OR DIRECTORY it doesn't meant THEY REALLY WANT to use CHMOD!  c'mon.

---

### Post by bobbob94 on 2007-04-27
To password protect a folder using Seahorse just do as i posted earlier "Start it up, and you create a key (Key>Create New Key>PGP Key) Once you've done this you should have an Encrypt option when you right click on a folder. Click this, then select the key you just made and it will produce an encrypted version of the folder called yourfoldername.zip.pgp, and there you go. You can also use your key to encrypt your email but thats a whole other topic!". 

However it does sound from what you said since then that you might be ok with changing permissions, as you're only trying to protect the folder from casual access. If that's all you need, pgp encryption or a truecrypt partition might not be necessary (though they're both fine and useful applications!). If you just create another user account for other users to log in with (call it guest or whatever) and you log out when you're not at your computer, then only you will be able to access your files. Other users can use your computer as guest, and you need your password to log on as you, after which you can see your files of course. Does that sound good enough?

---

### Post by bodhi.zazen on 2007-04-27
> **bobbob94 said:**
> However it does sound from what you said since then that you might be ok with changing permissions, as you're only trying to protect the folder from casual access. If that's all you need, pgp encryption or a truecrypt partition might not be necessary (though they're both fine and useful applications!). If you just create another user account for other users to log in with (call it guest or whatever) and you log out when you're not at your computer, then only you will be able to access your files. Other users can use your computer as guest, and you need your password to log on as you, after which you can see your files of course. Does that sound good enough?

frog3764, you have been given a lot of god advice regarding encryption by the community. I have been the advocate of permissions and here is why :

[list=number][*]You can do it NOW.[*]It is simple.[*]Unix (Linux/Ubuntu) is built from day 1 to be a multi user environment and thus permissions. Permissions restrict access as bobbob94 indicates and although not password protected are "tried and true".[/list]

I would take a fairly experienced "hacker" to get around permissions of 700.

From here : [http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

> Simply put, for each file it can be specified who can read or write from/to the file. For programs or scripts it also can be set if they are allowed to be executed.

Migrating to Linux takes time. Since you are not following the advice on encryption as of yet, go with permissions. Read and learn a little about the command line and encryption. Once the Light Bulb goes off so to say, and you successfully follow one of these encryption method you will have what you want and you can convert your directory (folder).

Encryption is not too difficult, but most do not consider it something new users find easy to do. Rather then beating you head against a wall, learn how you new OS is designed and use the easily available tools first.

just my 2c there :lolflag:

My advice in terms of encryption is : Choose a method, follow a specific, detailed how to, and ask specific questions when you get struck.

Examples:

I am following xyz. I put command abc into the terminal and I get this error message ???

OK I follow all those commands, I got no error messages, I generated a key, now what ?


Jumping from method to method is not such a good idea.

---

### Post by leibowitz on 2007-04-27
Yep, bodhi.zazen. Permissions is really simplier.

1° you need a password to enter your session. 

2° if your password is verified, you can access your files.

3° each file and folders permissions can be changed by three type of owners.
_ an user
_ members of a group
_ everyone else

4° set your permissions like you want. By default your user is the only one to be able to delete or write into your files. If you don't want anyone else to be able to read those files, then you need to check:
_ that everyone using your computer is identified. That means each person, or group of users, have an user/password on the computer.
_ that no one has access to your user/password.

5° If all of the precedent has been checked, then just set your folder permissions to 700 by going to Applications Menu > Accessories > Terminal. And paste the following command. Do not forget to replace **directoryname** by the directory path/name.
```
chmod 700 directoryname 
```

6° Then you can set permissions into the directory for files to 600.
[COLOR="Red"]Warning:[/COLOR] the content of the directory should be restricted to files for this command. If your directory contains sub-folders, then those sub-folders won't be accessible anymore. Please adapt to your situation.
```
chmod 600 directoryname/* 
```

---

### Post by frog3764 on 2007-04-27
Hey bobbob94 - I tried you method, made the pgp encryption key etc.  So now I have the file which I need to password etc to open, but it also creates a regular zip folder too.  After I encrypt it when finished reading it, the regular zip folder is still  there and can be opened up with no password.  I might be close here, but there must be something wrong.  Do I need to trash the regular folder when finished using it which would leave only the encrypted version requiring a password which would be OK I guess.

Frog

---

### Post by bobbob94 on 2007-04-28
Yeah, you can just delete the regular zip file and leave the pgp one. Of course don't just leave it in your wastebasket if you want it to be secure! Maybe you already know this but there's an option in nautilus (the file manager program that launches whenever you open a folder) to have a delete option on your right click menu that bypasses the wastebasket and properly deletes things straight away.  Edit>Preferences>Behaviour Tab> Tick box for "include a delete command that bypasses deleted items folder. Glad you got there in the end! :)  If you have the time though, do check out the good advice on this thread about permissions and users, as it's a good approach to these kind of problems too, and it's useful to know how that stuff works...

---

### Post by frog3764 on 2007-04-28
T H A N K S  to all who helped me with this mess.  And 94, this was sure a problem, at least on my end.  So I guess I finally got it figured out and it will work just fine.  

Thanks again to all
Frog

PS  I'll be back with another problem sooner or later!

---

### Post by fakie_flip on 2007-04-30
> **bobbob94 said:**
> Yeah, you can just delete the regular zip file and leave the pgp one. Of course don't just leave it in your wastebasket if you want it to be secure! Maybe you already know this but there's an option in nautilus (the file manager program that launches whenever you open a folder) to have a delete option on your right click menu that bypasses the wastebasket and properly deletes things straight away.  Edit>Preferences>Behaviour Tab> Tick box for "include a delete command that bypasses deleted items folder. Glad you got there in the end! :)  If you have the time though, do check out the good advice on this thread about permissions and users, as it's a good approach to these kind of problems too, and it's useful to know how that stuff works...

There is a better way to delete stuff immediately without it going to the wastebasket. Highlight the item or items you want to delete, and push shift+delete. That will delete it/them immediately. Pushing the delete key by itself will send an item or items to the wastebasket.

---

### Post by fakie_flip on 2007-04-30
If you like encryption, you should also try Truecrypt. Google for Truecrypt's website and download a deb from it that works in Ubuntu. Truecrypt is awesome!

---

### Post by frog3764 on 2007-04-30
Thanks Flip for the update.  I'll just do that.

Frog

---

### Post by bodhi.zazen on 2007-04-30
LOL :lolflag:

How to Truecrypt : [http://doc.gwos.org/index.php/TrueCrypt](http://doc.gwos.org/index.php/TrueCrypt)

---

### Post by frog3764 on 2007-04-30
Thanks Bodhi - this look interesting.  I will have to study this.  It sounds easier and better than the Seahorse.

Frog

---

### Post by aberadam on 2007-09-09
I'm interested in this and sympathise with the OP. 

I want a folder that needs a password to get into.  That's it.  

No permissions changing because I'm a newbie and don't understand permissions, and frankly don't care.  I have to type my root access to install and download stuff, it's a very simple password, my first name so not secure!  No guest accounts because only I use the computer.  Not encrypted because I'm not a spy/paedophile. 

A folder with a password that is not my root/administrator password/account (because that's not even remotely secure).  

Is it possible?  

My mobile has a password to start up.  My phone can do it, can Ubuntu?

---

### Post by robert_pectol on 2007-09-09
Guys, listen...  trying to protect a file or directory from unauthorized access, simply by altering the permissions does NOT truly protect it!  Go ahead and pop a live CD in, boot up and see just how easily accessed your, "protected" file or directory is from anyone with a live CD!  It does NOT take an, "experienced hacker" to do that!  It's a false sense of security if you think the contents cannot be retrieved.  The only feasible way to protect your file/directory from unauthorized access is strong encryption, period!  I know it was mentioned in previous posts but I want to make the point very clear.  Use encryption!

There are various utilities and tools available to accomplish encryption, from encrypting single files to whole volumes.  Google dm-crypt, luks, and truecrypt, for more info.  As stated in previous posts, truecrypt is a good choice for ease of use, and interoperability among OSes.  There are even some front ends that make using truecrypt easier.  In fact, I wrote a simple one a couple of years ago called, "tcmounter" that I still use today!

But please, don't blindly rely on permissions for protecting sensitive data from unauthorized access!

---

