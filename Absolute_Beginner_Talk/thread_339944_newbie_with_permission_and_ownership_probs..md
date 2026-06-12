---
title: "newbie with permission and ownership probs."
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-01-16
Hi all,

I have searched for and read threads on permissions and ownership.

i am still lost.

I added 4 users to my ubuntu set up.

one of them wanted to work on his files. but he cannot access them, he has no permission. he is not the owner..etc etc etc

from my login he can do it.

the reason i added the 4 new users is so the entire fmaily does not use my login...

so what can i do so each user can save, delet, read, access in general their own files.?

Thanks

Robi from Budapest

---

### Post by taurus on 2007-01-16
What's the output of this command from a terminal?

```
ls -la /home
```

---

### Post by beanco on 2007-01-16
robi@robi:~$ ls -la /home
total 32
drwxr-xr-x  8 root  root  4096 2007-01-16 07:07 .
drwxr-xr-x 21 root  root  4096 2006-12-29 19:15 ..
drwxr-xr-x  2 abuci abuci 4096 2007-01-16 07:07 abuci
drwxr-xr-x 14 ancsi ancsi 4096 2007-01-16 18:57 ancsi
drwxr-xr-x 17 aron  aron  4096 2007-01-16 19:51 aron
drwxr-xr-x  3 evi   evi   4096 2007-01-16 07:41 evi
drwxr-xr-x  6 mauzi mauzi 4096 2007-01-02 19:25 mauzi
drwxrwxrwx 32 robi  robi  4096 2007-01-16 19:36 robi


is what I got

---

### Post by taurus on 2007-01-16
Looks like everything is in order there.  So you say that when aron logs in with aron as his username and his password, he can't write anything in his own $HOME directory, /home/aron!

```
ls -la /home/aron
```

---

### Post by hal10000 on 2007-01-16
right click to the files that can not be accessed. go to permissions and see who's the owner of this file. ALso have a look if it is readable for the owner

---

### Post by Delkster on 2007-01-16
> **beanco said:**
> so what can i do so each user can save, delet, read, access in general their own files.?

By "their own files", do you mean files located in their home folder, namely /home/username? How did these files come to the system? If you copied them from somewhere with your own account, they may have been set to be owned by you since, technically, in that case you'd be the one who created the files in the system.

If the files are located in each user's home folder (where they should be), you could try the following to force the ownership of all files in each user's home folder to be assigned to that user:
```

sudo chown -R abuci:abuci /home/abuci
sudo chown -R ancsi:ancsi /home/ancsi

```
... and so on.

Explanation:
"chown <user>:<group> <filename>" sets the file specified by <filename> so that it's owned by <user> and the group <group>. The option -R after chown and before the username means that the ownership of all files within the specified directory should be changed recursively.

Root privileges, in this case by means of sudo, are needed for the commands.

Be careful with the user, group and directory names.

---

### Post by beanco on 2007-01-17
I copied files for two of them. evi and aron from my home as that is where they had originall stored them.

so that means I copied my permissions, rights, whatever when I did so...

I will try to force the changes you suggest when I get home.

If I understand ocrrectly any file they create in their home folders themselves will be ok, ie. they will have full access to them...



what should I becareful of  concerning user, group and directory names?

and thanks!

Robi

---

### Post by hal10000 on 2007-01-17
After you copied a file from your own to the home directory of others you should change the permissions or make th other user the owner of this
file: [COLOR="Red"]sudo chown otheruser /home/otheruser/filename[/COLOR]

---

### Post by beanco on 2007-01-17
> **hal10000 said:**
> After you copied a file from your own to the home directory of others you should change the permissions or make th other user the owner of this
file: [COLOR="Red"]sudo chown otheruser /home/otheruser/filename[/COLOR]

thanks

i will try it.

robi

---

### Post by beanco on 2007-01-17
that was fairly simple. thanks

it seems to be working!!!

i am no longe the owner, Aron is, I logged on to his accounnt and could open, edit, etc the file.s


but now I cannot from my own account.

it is problably very simple but I am too tired and stupid to think abou tit now.. but how can i keep my permissions/rights to it?

robi

---

### Post by taurus on 2007-01-17
Basically, you two should belong to the same group.  Then, change the permissions so to group so the people on that same group can edit it.

---

### Post by beanco on 2007-01-17
how?

I am a toatl beginner at this stuff and sometimes even the basic stuff is beyond me...

robi

---

### Post by dorcssa on 2007-01-17
Go to Nautilus, click properties, go to permissions, and there you can choose the file's group. You can create new groups in system>administration>users and groups.

(In hungarian: a file tulajdnoságain belül a jogosultságoknál ott van egy lenyíló menü, h file csportja, ott tudod beállítani. És az adminisztrációnál a felhasználók és csoportoknál tudsz új csoportot csinálni ;) :D )

---

### Post by beanco on 2007-01-18
thanks Dorcsa,

Koszi! Bar nem vagyok magyar ajku azert ertettem amit irtal... koszi


robi

---

### Post by dorcssa on 2007-01-18
> **beanco said:**
> thanks Dorcsa,

Koszi! Bar nem vagyok magyar ajku azert ertettem amit irtal... koszi


robi

Hmm, pedig eléggé magyar neved van.. :D Örülök h segíthettem. :)

---

### Post by beanco on 2007-01-18
> **dorcssa said:**
> Hmm, pedig eléggé magyar neved van.. :D Örülök h segíthettem. :)


robert grady dawson a nevem... de itt mindki robinak szolit....

hogy van az hogy sok magyar foglalkozi az ubuntuval.


robi

---

### Post by Oki on 2007-01-18
Please write in English so we others can learn from it – I guess it is not so important but even though.  All tips are good for noobs like me. At least translate it. 

This would be uncool of me to do; Tenk hvis jeg skulle begynne å skrive norsk, da forstår dere heller lite …

---

### Post by beanco on 2007-01-18
> **Oki said:**
> Please write in English so we others can learn from it – I guess it is not so important but even though.  All tips are good for noobs like me. At least translate it. 

This would be uncool of me to do; Tenk hvis jeg skulle begynne å skrive norsk, da forstår dere heller lite …

would that be in  Nu Norsk or bukmal?

But you are right, we should use Eng sinc ethis is the English forum...

All she wrotein the first Hungarian bit was the same as the Eng, then I replied saying thanks and that I cna read it even though I am not Hungarian.

now back to our regularly scheduled thread...

robi

---

### Post by dorcssa on 2007-01-18
> **beanco said:**
> robert grady dawson a nevem... de itt mindki robinak szolit....

hogy van az hogy sok magyar foglalkozi az ubuntuval.


robi

Look at this: [http://ubuntu.hu/forum/index.php](http://ubuntu.hu/forum/index.php) Not so much ctiv member though.(including me: ) )

Oki: sorry for not writing in english, but I was so glad to see someone here who actually lives where I live. And my words was only offtopic. ;)

---

### Post by beanco on 2007-01-19
> **dorcssa said:**
> Go to Nautilus, click properties, go to permissions, and there you can choose the file's group. You can create new groups in system>administration>users and groups.

.....


so wha tis the nautilus of which you speak Dorcsa? I mean how to go there?

I want to be able to access all the files on this computer, regardless of whose it is.

how can I do that?

Anybody?
robi

---

### Post by Delkster on 2007-01-19
> **beanco said:**
> so wha tis the nautilus of which you speak Dorcsa? I mean how to go there?

Nautilus is the name of the standard file manager in Ubuntu. When you open a location or folder, you open it in Nautilus.

> I want to be able to access all the files on this computer, regardless of whose it is.

I don't have time right now but I'll get back to that a little later. To put it short, you have three options:

1. Sharing a common group for all users. Every file has an owner and a group designation, and access permissions can be set separately for the owner, the file's designated group, and all others. If everyone belongs to a group, for example "users" (in fact that group probably exists in Ubuntu already), you can set everyone's files so that they're owned by the user herself but that their group designation is "users". Then you can change the access permissions so that not only the owner but also the group (or actually all its members) have certain permissions to the file, for example reading it or writing (modifying) it.

The group designation and the permissions of a file can only be changed by the user who owns the file, so in stage you'll need to be logged in by the users whose files' permissions you're changing. After the files have been set to a certain group, the permissions made so that they allow the group to access the files, and you belong to that group, you can access the files.

The downside is that the group id and the permissions don't carry on to newly created files, so you'd have to do that to new files as well.

2. Same as above, but tweak things so that newly created files within the users' home directories automagically "inherit" the group id from their "parent" folder, and set each user's so-called umask so that all newly created files have their permissions set to allow the group to access the files. This takes some tweaking on the command line with advanced tricks on the permissions. It *should* be possible, though (I haven't tried it myself in this context), and I can try to help you with that, but I don't have time for that right now.

Edit: Actually, changing the other users' primary group to "users" in Users and Groups would probably also make their newly created files appear with the group designation "users", so that part wouldn't even require significant magic with the permissions. Anyway, I'll check this out later.

3. On your user account's desktop, have an icon or something that opens the file manager with administrative privileges. With those privileges you can read and write practically everything regardless of the ownership, group designation or access permissions of the files.

---

### Post by beanco on 2007-01-19
Thanks Delkster,

I will try and decipher just what you are writing...

robi

---

