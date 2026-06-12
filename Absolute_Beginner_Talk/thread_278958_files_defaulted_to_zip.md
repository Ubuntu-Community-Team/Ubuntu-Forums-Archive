---
title: "files defaulted to zip?"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-10-17
Hi everyone, as per my last post on this, I've now spent many hours reading and reading and searching. I'm afraid I can't find anywhere why my newly created files are defaulting to zip files. I'd like to find out why so it doesn't happen again and also how to fix those that have been inflicted.](*,)
I have managed to discover some answers for other problems but not this one.
All advice appreciated

---

### Post by Arby on 2006-10-17
Ok, without knowing how you created the files I have no idea why they are defaulting to zip files. To unzip the ones you have it's as simple as ```
unzip myfile
```type man unzip at the commandline for full details.

---

### Post by CatKiller on 2006-10-17
Are they actually zip files or just pictures of zip files? If you right-click on them and select Properties, what does it say under Type and MIME type?

---

### Post by carloslosgrande on 2006-10-17
Hi Catkiller, in properties it says;
type; ZIP archive
MIME type; application/zip

thanks Arby, I can actually open them with other apps as I want but i can't post them here and it also means that I'll have difficulty when real ZIP files need action, if you know what i mean? (not sure I do).

---

### Post by Arby on 2006-10-17
> **carloslosgrande said:**
> Hi Catkiller, in properties it says;
type; ZIP archive
MIME type; application/zip

thanks Arby, I can actually open them with other apps as I want but i can't post them here and it also means that I'll have difficulty when real ZIP files need action, if you know what i mean? (not sure I do).

I'm not sure what you mean. If their type is zip archive then they are 'real' zip files. Besides if you ever do have 'real' zip files then unzip will still unzip them for you. I'm afraid you've lost me there.

However, none of this explains why they got created as zip files in the first place if you didn't ask for that. So, what are these files? where did they come fom, how did you save them, with what apps etc? Give us more information and maybe we can find out what's happening. In the original post you mentioned 'as per my previous post', a link would be helpful here

---

### Post by CatKiller on 2006-10-17
Freaky. Looks like you've messed up your MIME settings in some way. You could try reading [this page]("http://linux.about.com/library/cmd/blcmdl5_gnome-vfs-mime.htm") to see if it sounds like anything that you've done. Or you could try forcefully reinstalling the gnome-mime-data package.

Fairly obviously I've not come across this before, so I have no idea if any of this will work for you. Let us know if you do fix it though, in case anyone else does the same.

Oh, and you could try creating a new user to see if that account has the same problems - single-user problems tend to be much easier to fix than system-wide ones.

---

### Post by carloslosgrande on 2006-10-18
Hi Catkiller, thanks for the info; I looked at the link you posted and even though most of it is beyond me I searched for the files indicated.
> Application that wish to install their own MIME types only need to install a file in this directory. 
The file /usr/share/mime-info/gnome.mime is special, as it contains the defaults for gnome, and is read first. In addition, the file ~/.gnome/mime-info/user.mime is read last. This will guarantee that there is a way to set system defaults, and there is a way for the user to override them. There is currently no way to tell anything about the order of the other files in those directories,
the > /mime-info file is there but the > /gnome.mime isn't. Therefore > /.gnome/mime-info/user.mime isn't either
I did find an odd thing in > /user/share/mime-info/openoffice.keys
category=Documents/Word Processor
	use_category_default=yes
	icon_filename=openofficeorg-20-oasis-text-template
application/vnd.oasis.opendocument.text     *no space*
	description=OpenDocument Text
	[en]description=OpenDocument Text
	[de]description=OpenDocument Text
	
	category=Documents/Word Processor
	use_category_default=yes
	icon_filename=openofficeorg-20-oasis-text
					*there is a space here*
application/vnd.oasis.opendocument.text-web
	description=HTML Document Template
	[en]description=HTML Document Template
	[de]description=HTML-Dokumentvorlage
	[ca]description=Plantilla de document HTML
	

	category=Documents/Word Processor
	use_category_default=yes
	icon_filename=openofficeorg-20-text-template
application/vnd.sun.xml.writer		*no space*
	description=OpenOffice.org Text Document
	[en]description=OpenOffice.org Text Document
	[de]description=OpenOffice.org Textdokument

there are no spaces in this part of the text only for the apps causing trouble. I have no idea if this matters. I changed it anyway - didn't seem to fix anything (restarted system).
set up new user - It doesn't have this problem!! so its only on my sign-in.
I'm not at all certain about how to forcefully reinstall?:confused: I take it there is a simple command?
Thanks for your help.

---

### Post by CatKiller on 2006-10-18
Given that it's only your user that's having the problem, you shouldn't need to reinstall anything, thankfully. My attempt at a fix would be to do ```
gksudo nautilus
``` to give you a file browser as root, Ctrl-H to show hidden files and then copy the user.mime file from the home folder of the user that works to the home folder of the user that doesn't, change the owner and group of that file to the user that doesn't work, log out and log back in.

It might not work, but the good thing about it only being one user that's affected is that it must be something in that user's home folder causing the problem.

---

### Post by carloslosgrande on 2006-10-18
Hi Catkiller, thanks for your help. I tried to follow your instructions but got stuck after the show hidden files bit, as you can see in the attachment, I can't see any usr.mime files there to copy?!:confused: 
So I used the flash disc and copied it that way. I reckon its the slow way but it got the job done.:D 
I rebooted the system and tested but its still saving Writer files as Zip. I can save them as RTF ok. I think the Win Doc file ext also defaults to Zip.
Needless to say its got me buggered!:rolleyes: 
I assume that the forced reinstall is my best option?
Sorry it takes so long between answers but I'm flat out with work.

Befuddled.

---

### Post by CatKiller on 2006-10-18
If it were there, it would be in /home/*username*/.gnome rather than in /root where you are in that screenshot. I don't know for sure that that is the file that you're looking for, nor if it should be there on an Ubuntu system. I'm pretty much as in the dark as you are.

---

### Post by CatKiller on 2006-10-18
OK - where we've got to so far. There is a file or group of files in your home folder that is broken. The equivalent file or group of files in the home folder of the user you created is not broken. By copying the files from the non-broken home folder to the broken home folder we might be able to fix the broken account.

Unfortunately, we don't know which file or group of files it at issue. I just checked, and I don't have a mime-info in my ~/.gnome.

However, I do have a ~/.local/share/mime, so you could try copying that across using the method above. Don't forget to right-click on the folder **after** you've copied it to your home folder to change the owner and group to you, otherwise you may break something else.

EDIT: You might not know that ~/ means the same as /home/<*username*/ and directories that start with a . are hidden. That's what the Ctrl-H is for. And the reason you're running Nautilus as root is because otherwise you can't read the other user's home directory.

---

### Post by carloslosgrande on 2006-10-19
I see now, that nautilus command lets me see files in both users! thats handy.
My gnome files are all under root/usr/share not in the home dir
thanks Catkiller (I like the name), maybe I'll have a look about the force reinstall thingy.:-k 
never say die.

Just looking around some more and in my user there are these (attached) mime files but they seem to be for firefox and I'm not actually sure just where they are.[2 of them are identical].

---

### Post by CatKiller on 2006-10-19
> **carloslosgrande said:**
> My gnome files are all under root/usr/share not in the home dir

That could be your problem. How about in the new user's home folder? Do they have files that you lack?

EDIT:> thanks Catkiller (I like the name)It's Cornish.

---

### Post by carloslosgrande on 2006-10-19
Hi Catkiller.
Ok, the other user has the same basic setup in that there are also no directories or files relating to mime in the homedir. actually the other user has very few directories or files at all. I have made the user but haven't set-up anything else for that user at all - no apps, repositories, etc.

An odd thing happened - When I use the gksudo nautilus command I get to the root dir but can't access home dir for either user. This morning when I signed in I had automatic access to view both user directories, but not the files except in the user sign-on I'm in. [the wording may be a little clumsy there].

Anyway the upshot is I can't copy from the home dir of the other user as it has no mime files.
If its essential to have mime files in my home directory, and I don't, surely I wouldn't be able to save any files?

---

### Post by CatKiller on 2006-10-19
> **carloslosgrande said:**
> Hi Catkiller.
Ok, the other user has the same basic setup in that there are also no directories or files relating to mime in the homedir. actually the other user has very few directories or files at all. I have made the user but haven't set-up anything else for that user at all - no apps, repositories, etc.

But you did create some files to establish that that user didn't have the same problem you did? And you did Ctrl-H to show the hidden files starting with . ? And you looked specifically in /home/*newuser*/.local/share?

> An odd thing happened - When I use the gksudo nautilus command I get to the root dir but can't access home dir for either user. 

That's peculiar - the superuser can view any file, pretty much by definition. What did it say?

> This morning when I signed in I had automatic access to view both user directories, but not the files except in the user sign-on I'm in. [the wording may be a little clumsy there].

That's the behaviour as it is supposed to be - the Home folder for each user is a private place where they can do whatever they want. So by default, only that user and the superuser get to see inside.

> Anyway the upshot is I can't copy from the home dir of the other user as it has no mime files.
If its essential to have mime files in my home directory, and I don't, surely I wouldn't be able to save any files?

You can still create files. That's a really fundamental thing. It's being able to identify the type of file that it is, and knowing what to do with it, that needs the MIME settings.

---

### Post by CatKiller on 2006-10-19
You may find [these GNOME pages]("http://www.gnome.org/learn/admin-guide/latest/mimetypes-0.html") of interest. They appear to describe how GNOME handles MIME types. I haven't read them myself.

---

### Post by carloslosgrande on 2006-10-20
Hi Catkiller, as far as I can see there is no dir called /home/newuser/.local/share, and yes I searched in the hidden folders [ctrl h].
yes I did make a new file, in the new user,and save it with no problems.
the gksudo nautilus command got me to sys files, root and desktop [which is empty] in that order, there wasn't any message, error or otherwise.
Yes I can still create files and I can save them in Rich Text Format without trouble. to save into XP doc it becomes mime type - application/ole-x-storage.
All the openoffice apps are defaulting to zip.
OK I'm going to go and have a read of the link you put in.
Thanks man.

---

### Post by CatKiller on 2006-10-20
> **carloslosgrande said:**
> Hi Catkiller, as far as I can see there is no dir called /home/newuser/.local/share, and yes I searched in the hidden folders [ctrl h].
yes I did make a new file, in the new user,and save it with no problems.

The *newuser* in the above line is representative of whatever you called your second, test, user. I don't know how clear that was.

> the gksudo nautilus command got me to sys files, root and desktop [which is empty] in that order, there wasn't any message, error or otherwise.

/root is root's Home folder. /home/newuser is the Home folder of your new, test user. /home/whatever-your-user-name-is is your Home folder.

> Yes I can still create files and I can save them in Rich Text Format without trouble. to save into XP doc it becomes mime type - application/ole-x-storage.
All the openoffice apps are defaulting to zip.
OK I'm going to go and have a read of the link you put in.
Thanks man.

Good luck.

---

### Post by carloslosgrande on 2006-10-20
Hi Catkiller, sorry about that obviously silly mistake, you were clear, I just wasn't thinking.:rolleyes: 
attached is the snapshot of the hidden files in the new user - no local dir
the link had a lot of info that I have difficulty following well enough to put ot use, other than the 'refresh mime files' command, which I did but without any noticable effect.
It seems my options are running out.:-k 
Thanks for your help.

---

### Post by CatKiller on 2006-10-20
> **carloslosgrande said:**
> It seems my options are running out.:-k 

I think this makes you the resident expert on MIME types in Gnome. As a not-very-good solution, you could start using the second user account instead, since that one works. When I get a bit more time I'll have a read of the pages I linked, in case anything occurs to me, but I'm now officially stumped.

---

### Post by carloslosgrande on 2006-10-21
Hi Catkiller, > **CatKiller said:**
> I think this makes you the resident expert on MIME types in Gnome.
now thats a worry!
I'm currently saving the files I want as rtf without any problems. I've searching some more but nothing like this has popped up yet.
I figure on updating to Edgy later on so i guess that'll fix it anyway?:rolleyes:
i just found this  > <mime-type type="application/vnd.sun.xml.writer.template">
    <sub-class-of type="application/zip"/>
    <comment>OpenOffice Writer template</comment>
    <comment xml:lang="bg">&#1064;&#1072;&#1073;&#1083;&#1086;&#1085;, &#1092;&#1086;&#1088;&#1084;&#1072;&#1090; OpenOffice.org Writer</comment>
    <comment xml:lang="de">OpenOffice·Writer-Dokumentenvorlage</comment>
    <comment xml:lang="nb">OpenOffice Writer-mal</comment>
    <comment xml:lang="no">OpenOffice Writer-mal</comment>
    <glob pattern="*.stw"/>
  </mime-type>
  <mime-type type="application/vnd.oasis.opendocument.text">
    <sub-class-of type="application/zip"/>
    <comment>ODT document</comment>
    <comment xml:lang="bg">&#1044;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;, &#1092;&#1086;&#1088;&#1084;&#1072;&#1090; ODT</comment>
    <comment xml:lang="de">ODT-Dokument</comment>
    <comment xml:lang="nb">ODT-dokument</comment>
    <comment xml:lang="no">ODT-dokument</comment>
    <acronym>ODT</acronym>
    <expanded-acronym>OpenDocument Text</expanded-acronym>
    <glob pattern="*.odt"/>
  </mime-type>
  <mime-type type="application/vnd.oasis.opendocument.text-template">
    <sub-class-of type="application/zip"/>
    <comment>ODT template</comment>
    <comment xml:lang="bg">&#1064;&#1072;&#1073;&#1083;&#1086;&#1085;, &#1092;&#1086;&#1088;&#1084;&#1072;&#1090; ODT</comment>
    <comment xml:lang="de">ODT-Vorlage</comment>
    <comment xml:lang="nb">ODT-mal</comment>
    <comment xml:lang="no">ODT-mal</comment>
    <acronym>OTT</acronym>
    <expanded-acronym>OpenDocument Text Template</expanded-acronym>
    <glob pattern="*.ott"/>
  </mime-type>
  <mime-type type="application/vnd.oasis.opendocument.text-web">
    <sub-class-of type="application/zip"/>
This is after running the mime update command, and it seems zip is the higher level? or am I misunderstanding?
this is in my ```
/usr/share/mime/packages/freedesktop.org.xml
```
this setting is only on the opendocument types, as far as I can see.

---

### Post by carloslosgrande on 2006-10-21
Hi, I'm thinking I should just take out the line that says <sub-class-of type="application/zip"/> as other apps don't have this line.
It seems to be the line causing the trouble. However, I still don't know where this line originated from.:-k

---

### Post by CatKiller on 2006-10-21
> **carloslosgrande said:**
> Hi, I'm thinking I should just take out the line that says <sub-class-of type="application/zip"/> as other apps don't have this line.
It seems to be the line causing the trouble. However, I still don't know where this line originated from.:-k

You might as well try - it certainly seems to be related to the problems you're experiencing. If you make a backup of the file first, then it shouldn't matter if taking those lines out breaks anything else. It's weird that your other user didn't have problems if the problem is with a file in /usr.

Let us know what happens.

---

### Post by carloslosgrande on 2006-10-23
Ok, current status is; removing the lines as per previous response has no effect on files mime type but does seem to have buggered up bzip2.
I restored those lines from the copy I took prior to removal, but bzip2 is unappreciative of this favour.
> bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.
It also seems to have an unexpected effect on automatix
 > Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  Could not connect to [www.getautomatix.com:80](www.getautomatix.com:80) (82.165.193.29), connection timed out
this is after several tries and a restart. I've run the mime update command - successfully i believe, but these new difficulties are clinging.

I tried to run the 'bzip2recover' program as indicated but it didn't seem to do anything, I probably didn't set up the command right. I also tried using that tvv option in this way ```
sudo aptitude update -tvv
```but there seemed no effect with this either:-k 

There may really be some fundamental setting that is now reset to something odd. Oops!
I've been meaning to reset the partition sizes anyway as that XP wont be needing much anymore, so I guess a reinstall may be coming up.
I'd better do some checking about that. As they say in China 'cha bu duo fan bu liao'
Thanks Catkiller

---

### Post by carloslosgrande on 2006-11-07
Ok, I couldn't find anything to lead me to what might have caused this problem, so I reinstalled from the live cd. Its all hunky dory now and the files that were zip I can now save as odt whatever, no trouble.
I assume it was some command I entered arse about or some such thing in the terminal as this seems the only likely cause to me.
Thanks to all for your help!:D

---

