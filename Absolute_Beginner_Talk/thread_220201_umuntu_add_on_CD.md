---
title: "umuntu add on CD"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-07-21
Still trying to get the MP3 to play ,,

The story so far;

Downloaded CD which has all the files I needed , follows the instuctions ,,CD in drive , software properties----> add CDRom , 

comes back with an error saying to put cd in drive ..( itd in there)

then it asks for a name for the cd

i type uppgrade  * enter* 

it returns error message code 2 

 E:sub-proccess gpvg returned an error code ( 2) W;signiture verification failed for cd/dist/dapper/release.gpg

I figured this was an saying a key was needed ,  now I followed the links in the web page , typed in the add to souses list 

permission denied 

back to square one 


Com on Fellas , ya cant say I aint tryin  ... 

you can see how long I have been at this 

Surely some one can help PLEASE ...

 I am a NEW USER to LINUX 

I WANT TO USE IT ,,, but if not happening by Sunday ,,, I ll shit can the whole thing , spent FAR to much time getting no where 

Stephen](*,) 

Using  Xubuntu on a pentium 3 with 128 ram at 650 MHZ

PPS Sorry admin , but I am going to keep posting new threads till this is solve Or untill sunday arrives

---

### Post by Skia_42 on 2006-07-21
Your desciption of the problem is rather cryptic, would you mind expalaining what mp3 you are trying to play and what you downloaded? e.t.c.

---

### Post by tuxinvader on 2006-07-21
Do you have internet access from this box? Why are you using a CDrom rather than the internet?

Can you post your /etc/apt/sources.list

What CD is it and where did you get it from?

---

### Post by basilwatson on 2006-07-21
I downloaded xunumtu, burn .iso , now have the laprop connected. to internet and no I cant get sources as I dont have permission 

Have spent last 2 hours reading linux basics how to ....and will try again

ANY MP3 would be fine 

I downloaded xmms. deb tried to install and it say it need another package...

Realaudio is a .bin file ..which wont extract in Xubuntu ...

Does this sound like a pissed off frustrated user ..thats because it is ..

I ll try to get the source file ...

ahhhhhhhhhhhhhhhggggggggggggggggg 


Stephen

---

### Post by basilwatson on 2006-07-21
right I tried sudo su /etc/apt/sources.list

sudo/etc/apt/sources.list

/etc/apt/sources.list

all permission denied 

how do I get permission 

chmod ???  but what do I type for this case 

Stephen

---

### Post by adam.tropics on 2006-07-21
sudo gedit /etc/apt/sources.list

gedit is the text editor, you have to tell it what to actually do with the file.

---

### Post by basilwatson on 2006-07-21
ok tried sudo gedit /etc/apt/sources.list

command not found

then  sudo su gedit /etc/apt/sources.list

and every combination there off /etc   then etc  havent tried ./etc

Next

Stephen

I am a new user ... like tring to get me to fix an engine when I dont know what a engine is

---

### Post by argie on 2006-07-21
use
```
sudo nano /etc/apt/sources.list
```
And enter your password. I thought gedit came with Ubuntu by default?

---

### Post by Qwerty_ on 2006-07-21
Gedit does coem standard with ubuntu.

---

### Post by basilwatson on 2006-07-21
sudo nano /etc/apt/sources.list

opened a terminal with writing at the bottom , tried typing  in stuff , and 

the commands at the bottom  such as ^G  or ^O and nothing happened 

opened another terminal with a tab and was back to permission denied 

Next 

Stephen

---

### Post by argie on 2006-07-21
^O means Ctrl+O . just telling you. It took me some time to figure out.

---

### Post by kagashe on 2006-07-21
Hi Stephen,

Perhaps by "add on CD" you mean the CD discussed in [this thread]("http://www.ubuntuforums.org/showthread.php?t=183933").

Because the error you are getting is same I got after adding this CD in Synaptic. You need to import the signature from the CD as follows:
> Click on System/Administration/Synaptic Package Manager.
Click on Settings/Repositories.
Click on Authentication Tab.
Click on Import Key File.
Click on CDROM on left panel(or go to /root/media/cdrom0)
Select file public.key
Click Ok.
Click on Edit/Add CDROM
Now you will not get any error.

Please read the thread for any other guidance.

kagashe

---

### Post by sharperguy on 2006-07-21
He is using xubuntu which is why he cant use gedit.

To install new software, the easyest way is to go to Applications>Add/Remove, with this you do not have to download the .deb files, it does it for you.

To install more software than Add/Remove offers you:

In Add/Remove, there should be a button that says "Go Advanced", click it. This will open up synaptic, the advaned package installer.

From there you can add lots of repositories for software not available by default in ubuntu.

Choose Settings>Repositories and hit Add.

Now choose all of the repositories, including the ones available from the drop down menu (for updates).

There is also an easy way to install mp3 codecs:

While your still in repositories, Add a custom one, and in the apt line box put:
```

[I]deb http://www.beerorkid.com/automatix/apt dapper main
```

Then press ok back to the main synaptic page.

Now do a search for Automatix, a program which helps you install things like flash. java, mp3 codecs, etc.

Install it by checking the box next to it and pressing apply.

After it has finished, close synaptic

There should now be a choice in the Applications menu for automatix. (in Ubuntu its Applications>System Tools>Automatix, but it could be different in xubuntu).

Open it and choose the things you need, press ok and let it install, you may have to give it your password.

Now you should be able to listen to mp3's with any music player.

[/I]

---

### Post by basilwatson on 2006-07-21
[COLOR="Navy"][SIZE="5"]A BIG THANK YOU FOR THAT[/SIZE][/COLOR]  I am now off and running, still havent heard any music yet but things are looking good 

discs are wirrring things are installing 

Big thank you ...

Life time supply of green BLING  goes you way 

Thank you from Japan !!!!

Stephen

---

