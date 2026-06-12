---
title: "i need dvd help please!"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Linux&amp;Lizards on 2006-10-05
ok.
i am in the process of switching from windows to linux.
I am currently using ubuntu 6.06 with the hope of being able to freely play and burn some dvds however i recieved this message today when i threw one in 


No URI handler implemented for "dvd".

what do i do?
i have no previus experiance with linux but im eager to learn!
can someone please give me some helpful pionters?

---

### Post by andlinux21 on 2006-10-05
try EasyUbuntu or Automatix it should help you on your quest just do a search of the forums.

---

### Post by Linux&amp;Lizards on 2006-10-05
> **andlinux21 said:**
> try EasyUbuntu or Automatix it should help you on your quest just do a search of the forums.

kk ill try that thanks

---

### Post by Linux&amp;Lizards on 2006-10-05
um how would i acess any of those programs u recomended?](*,)

---

### Post by podunk on 2006-10-05
[http://www.getautomatix.com/](http://www.getautomatix.com/)

:-)

You need to install the  "Nonfree codecs" to make DVDs work. Check out streamtuner and xmms while you're there.

Welcome! 

I see you've met our mascot already  ---> ](*,)

---

### Post by Linux&amp;Lizards on 2006-10-05
ok i believe i installed easy ubuntu right.

however when i try to play dvds now i get this message 
totem canot play this type of media (dvd) because you do not have the right plug ins to handle it 
Please install the necessary plugins and restart Totem to be able to play this media


what should i do and how?............:cool:

---

### Post by Linux&amp;Lizards on 2006-10-05
please!
what should i do to get the plug-ins
i would really like to get this fixed asap.


i tried suse for awhile and bothered with xine and kaffien before losing it lol.


UBUNTU ROCKS!

---

### Post by corstar on 2006-10-06
Make sure you have all the backport repositories enabled (in synaptic) 
Then get the gstreamer good, bad and ugly codecs.
Also get libxine extra codecs.  If you use konqourer to browse local stuff, you will need to get libarts1-xine to be able to see video thumbnails in it.

I also recomend getting the gstreamer-xine instead of using gstreamer totem. 

Oh, and most importantly, get the win32 codecs from the mplayer website and install them to 
/usr/lib/win32   you will need to sudo or be root for that.

Hope it all works out for you.

---

### Post by Linux&amp;Lizards on 2006-10-06
thanx ill try that

---

### Post by Linux&amp;Lizards on 2006-10-06
hey guys.

how would i acomplish what he just said?
like i said im new and dont know very much about linux so i dont have a clue about how to do what he just said.

---

### Post by Linux&amp;Lizards on 2006-10-06
SO
would it be easyer just to get mplayer?
and if it is will someone pleae guid me through the installation process

---

### Post by Linux&amp;Lizards on 2006-10-06
so um.
what do i do next is there a better os out there for multi media use?

and if yes how would i ubtain it

---

### Post by Linux&amp;Lizards on 2006-10-06
...

---

### Post by gn2 on 2006-10-06
Go to [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38) and follow the instructions at number 4, for the automatic install.

Automatix is a utility that will help to install everything you need to play DVD's, and a host of other goodies that don't come with a standard Ubuntu install.

Alternatively try PCLinuxOS, I've found it's a much easier Distro for a Linux beginner.

---

### Post by Linux&amp;Lizards on 2006-10-06
thanks ill check into that right away

---

### Post by peteros on 2006-10-06
Try using the software downloader to load VLC media player. This will play all codecs. You have to use option for other. Will download and install.

---

### Post by Linux&amp;Lizards on 2006-10-07
um i live in alaska is it legal to install automatix?

isnt easyubuntu kind of the same thing?

---

### Post by Linux&amp;Lizards on 2006-10-07
okay im trying to get the vlc media player but it says this on its download page


A fairly recent version (between 0.8.1 and 0.8.2) is packaged in Sarge. However, if you want libdvdcss (DVD decryption) support, you will need to add the following lines to your /etc/apt/sources.list:


how would i do that?

like i said im new to linux.

---

### Post by gn2 on 2006-10-07
> **Linux&Lizards said:**
> um i live in alaska is it legal to install automatix?

isnt easyubuntu kind of the same thing?

Don't think the FBI are going to come knocking at your door to stop you watching DVD's on your PC, they've got more pressing things to attend to right now...

---

### Post by Linux&amp;Lizards on 2006-10-07
hey guys i installed atomatix and i am trying to get it to run ill let you know how it goes and thanx for all the help you guys have been gr8.  :)

---

### Post by Linux&amp;Lizards on 2006-10-07
it said it was illegal to use win32, and wine along with other non-free codecs and that it concerned the authoriteis.
what does that meen?

what shold i do?
is it illegal?
or does it just say that?
i thought linux was shareware
i dont whant to get in trouble will I?

so far u guys have been gr8 and this looks like what ive always wanted i just dont want to break any laws

---

### Post by Linux&amp;Lizards on 2006-10-07
> **gn2 said:**
> Don't think the FBI are going to come knocking at your door to stop you watching DVD's on your PC, they've got more pressing things to attend to right now...
 yeh but the cops might but that still doesnt answer my quetion IS IT ILLEGAL?
my uncle who llives in newport had some of his friends get locked upp because they were copying dvds

---

### Post by gn2 on 2006-10-07
> **Linux&Lizards said:**
> it said it was illegal to use win32 along with other free codecs and that it concerned the authoriteis.

what shold i do?
is it illegal?
or does it just say that?
i thought linux was shareware
i dont whant to get in trouble will I?

All these codecs and stuff come bundled with other Linux Distros.
If you had decided to download install and use PCLinuxOS for example you wouldn't even have to bother adding the extras...(other than lib2dvdcss)

Don't remember hearing about a US Government Agency trying to shut PCLinuxOS down......

---

### Post by gn2 on 2006-10-07
> **Linux&Lizards said:**
> yeh but the cops might but that still doesnt answer my quetion IS IT ILLEGAL?
my uncle who llives in newport had some of his friends get locked upp because they were copying dvds

Copying DVD's is illegal, viewing them isn't.

The dudes that got locked up were probably selling the copied DVD's methinks.
Which is a crime (felony?)

---

### Post by Linux&amp;Lizards on 2006-10-07
ok thank you soooooooooooooooooooooooo very much for your help i think im getting this program to work.
and i agree with you about copying dvds thanks for all the help gn2 you made my life easier. :) :) :) :):KS

---

### Post by Linux&amp;Lizards on 2006-10-07
geez how long can this take to install?

well i guess it is a small price to pay for being able to watch any dvds i want to lol

---

### Post by Linux&amp;Lizards on 2006-10-07
hey it works gr8!
i love it!!!!!
ty so much everybody:D :D :D :D :D :KS :KS

---

### Post by corstar on 2006-10-09
Well, to use Synaptic(which is basically one big installation manager for ubuntu) go to System=>Administration=>package manager. Open it up.
Click on the settings menu and find "repositories". click on that.
you will see a bunch of unchecked boxes. just click on them all then click ok.

quit synaptic then open up a terminal. 

type this command into the terminal.
sudo apt-get update

It will prompt you for your password, enter it and it will find the new packages you have just enabled in synaptic.

Right, that will take a few minutes, or more if you have dial up.
reopen synaptic and search for the packages I mentioned in the above post.

Also, I would recomend adjusting the settings in synaptic, like in the middle it has "consider recommending blah, blah " click that, that will get any dependednt or recomended packages.

here's a couple of  tips, whenever you get around to compiling software from source. It really is pretty easy.
   *if you get errors when configuring, try searching for the "dev" (develepment)     
    files and install them. 
This took me a little while get a grasp on, but I never have library dependency issues anymore

Compiling from source lets you have a newer version of the program. So, the meathod is uncompress the downloaded file somewhere, type "configure" (without quotation marks) then "make" and change to su (super user) and type "make install"

Sorry, if this seems a bit scatered, I'm not the best at writting tutorials.

So have a go at compiling from source one day, you won't look back once you've done it successfuly.

Let us know how you go with the codecs issue as well.

---

### Post by Linux&amp;Lizards on 2006-10-09
it went GREAT!!!!!
i have all the codecs and media player i could ever want u guys are the best.
THANKS FOR ALL THE HELP I RECIEVED FROM YOU GUYS.:KS :KS :p :D ;) :) :rolleyes: :cool:

---

### Post by Cpennyspal on 2007-02-25
> **Linux&Lizards said:**
> ok.
i am in the process of switching from windows to linux.
I am currently using ubuntu 6.06 with the hope of being able to freely play and burn some dvds however i recieved this message today when i threw one in 


No URI handler implemented for "dvd".

what do i do?
i have no previus experiance with linux but im eager to learn!
can someone please give me some helpful pionters?

Linus&Lizards,

I have the same problem.  I get the same message.  It says I must 
install Totem plug ins, but I don't have a clue where to get the plug ins or
how to install them.   I don't know how to use the forums and I'm getting 
frustrated.  The only thing I'm able to do is use the internet with Firefox.
 I don't even know how to submit an inquiry to get the proper answers.
Good luck!  
Ed (Cpennyspal)

---

### Post by Maestro23 on 2007-02-25
> **Cpennyspal said:**
> Linus&Lizards,

I have the same problem.  I get the same message.  It says I must 
install Totem plug ins, but I don't have a clue where to get the plug ins or
how to install them.   I don't know how to use the forums and I'm getting 
frustrated.  The only thing I'm able to do is use the internet with Firefox.
 I don't even know how to submit an inquiry to get the proper answers.
Good luck!  
Ed (Cpennyspal)

You need Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And as for making a new thread:  There is a big orange button at the top left of the forums.[COLOR="SandyBrown"] MAKE NEW POST[/COLOR]

Some links to introduce you to how things are done in Ubuntu:

> How to Install in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)


PS. Typing in big bold letters is not a way to get help faster.  Good luck.

---

### Post by Cpennyspal on 2007-02-25
[B][SIZE="4"] HELP!!!

I've installed Ubuntu and cannot get Totem to play a DVD.  I get a message that says
I must install necessary plug ins for Totem.  I don't have a clue where to get the plug ins
or how to install if I find them.

 Can someone tell me where I can find the plug ins for Totem and how to install them?

  I want to get away from Microsoft Windows because It keeps freezing up and shutting
 down all of the time.  

 P.S. ...I have a new computer and high speed DSL connection.

  Thanks,

 Ed (Cpennyspal)

[/SIZE][/B]

---

