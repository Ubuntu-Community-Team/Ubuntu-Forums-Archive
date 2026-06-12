---
title: "I cannot get internet connection"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by waterripples on 2008-02-09
****

Hello, I am very new to this. I been trying out Ubuntu booting from the cd. I like what I see but I cannot get online. Here are my details:  Dell Dimension 2400 pc 160GB hard disk-I am one of 5 computers in the house that runs off a linksys 801.11 router. Im using a Belkin wireless G card in my desktop. I have no clue what I am doing and in certain topics in the documentation site, I am beginning to wonder if they are talking of a previous or later version of Ubuntu because by what they describe I dont see. I dont see two computers on top of the other or where is this notification tab?> Im very lost and all I want is to be free of windows and use Ubuntu can anyone please help me???
Very frustrated Please

---

### Post by jan quark on 2008-02-09
hi " very frustrated"

you are not alone 
wlan can be sometimes tricky on linux

the two monitors over each other are probably the network manager icon see picture

pls post the output of the following terminal commands
to get some detailed info about your network card and status
```

iwconfig
```
```

sudo iwlist scan
```

```
ifconfig
```
```

lspci
```
```

sudo lshw -C network
```

---

### Post by pmshirey on 2008-02-09
Here are some basic steps:

[LIST=1]
[*]Try getting a connection with an ethernet cord
[*]If that doesn't work go into windows (or another computer) and type the i.p address of you ethernet passport or router and access the passport or router
[*]Make sure the passport or router will allow your computer to access the network.
[/LIST]

---

### Post by waterripples on 2008-02-09
what? i typed in those commands now what it just bringe me numbers and stuff im supposed 2 copy and paste all that? i cant im on 2 computers i dont know how 2 save all that as a file what do u need to understand my equiptment?

---

### Post by jan quark on 2008-02-09
hmmm you can save the output to a text file and "transfer" it walking from one pc to the other with the internet connection
do you have a usb stick or a floppy disc?

---

### Post by waterripples on 2008-02-09
yeah i saved it on text file

---

### Post by waterripples on 2008-02-09
no i thought i did but utumbu failed to save it to my stick. im lovin this

---

### Post by waterripples on 2008-02-09
you people must be computers yourself. I dont see how anyone can comprehend all this stuff. LOL What ever happened to Horse and Buggy? LOL Hopeless over here

---

### Post by waterripples on 2008-02-09
omg I just wanna use the internet with a cool looking utumbu, Im asking for the red pill but you guys gotta shove it in my mouth i dont know how to take it. I think I need a walk

---

### Post by waterripples on 2008-02-09
i dont wanna use ethernet i want my computer to use wireless like it does everyday with no issues

---

### Post by pmshirey on 2008-02-09
> **waterripples said:**
> what? i typed in those commands now what it just bringe me numbers and stuff im supposed 2 copy and paste all that? i cant im on 2 computers i dont know how 2 save all that as a file what do u need to understand my equiptment?

YOU HAVE NO CLUE WHAT I WAS TALKING ABOUT OMG!!!

---

### Post by waterripples on 2008-02-09
I give up, Calling geek squad its not worth the headache when its 100 questions i dont know the answer to. Thanks everyone take care

---

### Post by halitech on 2008-02-09
waterripples, I know you are frustrated right now and honestly, if you want to stay with Windows, that is your right. If you want to give Ubuntu a shot, maybe take that walk you mentioned and clear your head, have a smoke (if you smoke), go out and listen to the birds then come back and we'll try again when you feel up to it.

---

### Post by waterripples on 2008-02-09
hey there calm down ok. Im NEW to this whole thing no need to get testy, and YES I DO NOT UNDERSTAND what you were talking about because A. Im NEW B. Im inexperienced C. Both A & B. Answer= D This is not easy for a newbie so naturally, I can get lost.  I am only human. Not a geek squad member

---

### Post by jan quark on 2008-02-09
once I read somewhere:

linux is very user-friendly but it chooses its friends very carefully

living proof

waterripples I am sorry that you decided to give up, linux is a wonderful system
but not all things in life are gained the easy way, you have to invest some energy to benefit   from the advantages linux offers

there is no "One_click" solution in linux and in the real life neither

you are always welcome to come back and try another approach

Regards
Jan Quark

---

### Post by waterripples on 2008-02-09
No i hate windows! I mean sure its easier and most of everything makes sense but I just no longer want to be a windows user. I want to be part of this team you guys have because people will actually talk to you and try to help. But noone can expect me to just know what all this stuff means. because i can look up what DNS means and its still MY RIGHT if i cant understand what the meaning means. Its just more complex than what I thought. Im not being a spoiled kid, i am merely stating that I DO NOT UNDERSTAND. Thats all plain and simple. you cant expect a 3rd grader to understand Socrates Philosophy, so you cant expect a novice to understand a computer program when he has been brainwashed by windows. When you tell a baby to come to mama you dont say excuse me infant report to your mother immediately or accept the consequences of your actions, sign here please if you understand______________________The infant will look at you and most likely start crying.

---

### Post by waterripples on 2008-02-09
No proof of nothing im sorry. I just dont have the TIME to spend on a program like everyone else. In my life Computers are not the main focus. My life consists of being a father to my kids and things like that. I cannot be expected to understand all this so fast, all i want is to get online LMAo i just dont see why it has 2 be so hard.

---

### Post by waterripples on 2008-02-09
and i dont look for the easy way out in LIFE just in computers because we as americans waste enough time on computers why must we waste more in figuring them out? I just wanna get online argggg!

---

### Post by jan quark on 2008-02-09
waterripples
thank you you teach as all a wonderful thing, namely we are the ones with the limited perspective

the users who are used to linux cannot transfer their understanding of "obvious" matters to the whole world and think everyone understand the computer language immediately

let me think for a while so I can prepare a understandable solution for you but please
answer this few questions so I have a rough picture:

1 You have Ubuntu installed already on one PC?
2. you have a working internet connection on another PC?
3 The installation of Ubuntu worked flawlessly and you did not encounter any error messages?

---

### Post by waterripples on 2008-02-09
That was the most genuine and considerate response yet. I solemly appreciate that to a higher degree. Thank you. 

I am running Ubuntu from the CD
so when the PC starts I use the boot from disk option.

Yes I have problem free internet connection in my home on my 2 computers and my 3 other roommates computers. we all use whatever wireless cards we have in our pcs to connect to the Linksys 802.11g router
The installation of ubuntu never happened as I am running it from a CD and not the Hard disk.

---

### Post by halitech on 2008-02-09
the main reason windows "makes sense" is because most of us that were brought up around computer were brought up around windows and bily bob has done a wonderful job of getting it installed almost everywhere. If we had been brought up with Linux and MS was trying to get in now with windows, most of us wouldn't have a clue, its all a matter of what we learn and know from an early age.  And its not that learning Linux or setting it up is "more complex", its a matter of us (ex windows users and hopefully soon to be ex users) training ourselves to not think in the window world and how things have been done. Its almost a case of we need to forget everything we know about how computers work so we can learn a new way of doing things.

Don't worry about not understanding everything someone posts to you, if you don't know, ask for clarification and we will try to explain it so you can understand it. I think sometimes we forget this is a global community where an expression that is common where I am has no meaning in another area and vice versa.

---

### Post by waterripples on 2008-02-09
Thats exactly what I am saying. I was windows brainwashed and its so hard to adjust. I want to be rid of windows, But in order for me to start I need to at least have internet. All I need is to get online and then Im fine I can fully destroy windows and use Ubuntu. I can figure everything else out on my own

---

### Post by jan quark on 2008-02-09
ok you are in the so called LIVE session of ubuntu

you boot from the CD and ubuntu does not use your hard drive but your memory the ram

but you can give us good pieces of information also from this live session

follow this easy steps and nothing can go awry, we need this basic info to help

1. open the applications menu in the upper panel
2. under accessories search for the terminal
3. run it
4. type in 
```
lshw -C network
```
consider that linux is case sensitive so the capital C is really a capital C and there a space after lshw and after C

the output should be short and it should give us the exact name of your wireless card
so fetch even a ol'pencil and write it down and tell us

---

### Post by halitech on 2008-02-09
> **waterripples said:**
>  I can figure everything else out on my own

don't get cocky on us now ;)

I know what you mean though, once the basics are working, other things can be dealt with little by little but no net is hard to deal with and can be a major obstacle.

---

### Post by waterripples on 2008-02-09
ok hang on im rebooting now thanks i hope you are still here

---

### Post by waterripples on 2008-02-09
i get an error message after rebooting it said  there was an error starting the GNOME settings daemon

---

### Post by waterripples on 2008-02-09
ok this is alot of stuff to type so here goes  heres what happened when i pressed the lshw -C network

Warning you should run this computer as a super user
network: 0
description: Wireless interface
product AR2413 802.11bg NIC
Vendor: Atheros Communications Inc
physical ID: 4
bus info pci@0000:01:04.0
Bla bla bla bla bla bla bla
need any more>?

---

### Post by tashmooclam on 2008-02-09
My post may not help, but for what it's worth.
Wireless in Ubuntu and Linux is either effortless or a pain, mostly depending on the wireless card.
I had a Dell laptop and the wireless card was Broadcom, and I was pulling my hair out until I just went on ebay and bought an Intel wirless card ($25) This solved the "problem" and I was wirless and good to go.
I suggest that the Live CD Ubuntu is a good way to "test" your wireless card. Google around to see which wireless pcmcia card works welll with Ubuntu, and spend the $25-30 on it. 
OR, wait a a couple of weeks for Walmart to sell the Everex laptop running a version of Ubuntu called gOS Rocket. It's half the price of an Ubuntu Dell.

---

### Post by waterripples on 2008-02-09
thanks I appreciate it but i want to be cheap and use the same card I have otherwise Im just gonna throw my computer out the window get my camping gear and Im going off the grid.

---

### Post by ugm6hr on 2008-02-09
@waterripples:
I would recommend not posting multiple times in quick succession.  You can edit previous posts if you need to add further information (see the edit button at the bottom-right of each post).

With regard to your specific problem - the GNOME error is nothing to worry about.

As for wifi - a simple fact might help:
Is it a USB wifi dongle or PCI internal desktop wifi card?

What we are trying to do is help you identify what hardware chipset is within the "Belkin" branded device.

You might be able to identify the important bits yourself with an example:
```
lshw -C network
  *-network:1
       description: Wireless interface
       product:** AR2413 802.11bg** NIC
       vendor: **Atheros** Communications, Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: wifi0
       version: 01
       serial: 00:19:7d:33:e4:13
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=ath_pci **ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

The bits of information in bold are important.

EDIT: Just seen your post with lshw output - you have the same chipset as my laptop.  This is good news.  It will work.  Confirm that the driver listed is ath_pci first.

If so - I need some info from your wifi router.
What encryption do you use - WEP / WPA / none?
Does your router broadcast its SSID?

If these 2 questions don't mean anything to you - try and describe how you connected (the first time) with Windows.  Did you click on the networking icon that said something like - *there are wifi networks available*?
Then did you select your router from a list by name?
Then did you have to put a password in?  How many digits was the password?

---

### Post by nynoah on 2008-02-09
water ripples has your computer ubuntu install ever been connected to the net ever?

---

### Post by waterripples on 2008-02-09
oooh i see  i just edit the postings lol Im new forgive me

---

### Post by waterripples on 2008-02-09
no it never has

---

### Post by waterripples on 2008-02-09
as for all those numbers im lost   its a belkin internal wireless g card

---

### Post by waterripples on 2008-02-09
ok that is cool but i dont know what to do with all that im so lost.  i see some broadcom stuff  33 mhz    32 bits    BCM4401 100 BASE-T
pci@0000:01:04 and bla bla bla thats all i get i dont get this stuff




IEEEE 802.11g

---

### Post by ugm6hr on 2008-02-09
> **waterripples said:**
> as for all those numbers im lost   its a belkin internal wireless g card

Re-read my earlier post.  Then compare the bold bits to the output from your computer.

Then read my EDIT at the bottom of my previous post.

Then repost.

---

### Post by nynoah on 2008-02-09
Ok well for Ubuntu.....when you have the computer first started up with Ubuntu say after an install or when you are just using the live disk.  It is best to be connected to the net.  That way your Ubuntu can communicate with the repositories that store all the information about your computer hardware.  You will then be able to pull down from the repositories the correct drivers that you will need to get your wireless working.  There are 1000's of wiresless cards out there.  It would be impossible to have the drivers for all of them on the install disk.  So you need to connect to the net via hard wire to get the correct one for your unique computer.

Understand why I say this.  Its not really Ubuntus fault.  We just need to get a hard wire connection so we can get the drivers for your wifi.

---

### Post by waterripples on 2008-02-09
but....i dont have a hard wire whatever. all i have here is wireless i guess i cant use it then. thanks anyways i wish i knew that a few hours ago so i wouldnt have wasted my time. thanks though

---

### Post by waterripples on 2008-02-09
Goodbye everyone thanks for trying sorry I was such a pain, but theres no way I am going to get this working. I just want the freekin program not the hassle. anyways thanks guys but I guess Im not tech enough to be part of your gang.

---

### Post by nynoah on 2008-02-09
is the wireless port in your house or is it a shared thing for you apartment complex?

---

### Post by jan quark on 2008-02-09
I hope you won't treasure this experience as a very negative one
we really wanted to help you

bye waterripples 
perhaps we will see us again

---

### Post by ugm6hr on 2008-02-09
> **waterripples said:**
> Goodbye everyone thanks for trying sorry I was such a pain, but theres no way I am going to get this working. I just want the freekin program not the hassle. anyways thanks guys but I guess Im not tech enough to be part of your gang.

I think you may be right.

Shame, really.  If the output you gave before was actually from your lshw output, then I suspect you just need to click in the right place to get connected.

But then you mention Broadcom later.  I can see you are lost.  Unfortunately, by posting every minute with partial information, you have also been misleading people trying to help you, and not helping yourself at all.

---

### Post by nynoah on 2008-02-09
my line of thinking was that she did not have the correct drives for her Wireless card.  OR was I thinking down the wrong path on that one?

---

### Post by ugm6hr on 2008-02-09
> **nynoah said:**
> my line of thinking was that she did not have the correct drives for her Wireless card.  OR was I thinking down the wrong path on that one?

If you read the earlier posted lshw - it is an Atheros PCI wifi card.

It is supported out-of-the-box in Gutsy (and Feisty) with Restricted Drivers (which automatically load with the LiveCD).

I know this - I have the same chipset.

I suspect the problem was that he/she had not found the Network Manager icon with the drop-down list of SSIDs.

---

### Post by nynoah on 2008-02-09
Ok well I hope I did not complicate your explanation to her.  Sorry if I did.

---

### Post by waterripples on 2008-02-09
I know u all tried to help me i really do, its just that i dont truly even understand what you guys are asking me to produce therefore I cant produce it  its just so much information. All I know is I have a dell computer 2400 dimension  I use a belkin wireless g card with a linksys router 802.11g the ROUTER is in my home but I do not have a speaking relationship with my roomate who has the router in his room so I cant go in there and do anything with it. All I can give you is the information I know. If you give me some steps I can go thru with it but I need to directly understand and interpret the steps being handed to me. I dont know all of your tech terms I dont know A B from C. I can only tell You what little I can find out.  I dont know what information you guys need. youre not helping by being extra specefic, but again you guys dont get paid to do this so i dont expect anything out of you. I appreciate the help, but it seems like noone understands that I just dont understand, plain and simple. I would like to but I need crumbs before I can swallow. I cant dive in. OMG i just want the internet to work LOL never have I had such a headache with anything other than my wife

---

### Post by nynoah on 2008-02-09
Don't worry.........the people here are great.  Everyone learns in a different way and sometimes we just need a different way to explain things.  

Ok  the main issue to over come is that you are not familiar with how Ubuntu is laid out.  We just need to explain where to find things and how we can solve your problem in ways that you can follow.  It will get easier as you go.  No worries,

---

### Post by waterripples on 2008-02-09
the saddest thing really is i genuinely want to be a part of this, I like the forum and Im sorry I dont use it as well as you experts might. Its my 1st day. This has been so frustrating. I will never wrap my head around the fact that Its this hard to get online. if its this hard for just that im beginning to wonder how hard everything else will be and if its even worth it. i only want linux because I want out of windows, Im against windows im sick of windows. I want to crossover but dont wanna be a computer geek and have to put my philisophical books down only to pick up computer manuals. I dont have time to fill my head with this stuff. I have a life outside of computers

i just wish u guys can say ok clik on this, then click on that enter this then press this. Instead
Its all search for this decode this understand this then take this from this add this subtract that and multiply it by 76

---

### Post by waterripples on 2008-02-09
thanks guys you tried its clear that i dont belong here. Im not super super tech Smart like you guys. Have fun being supreme above all. :)
I do appreciate all the help, even though it didnt help lol I appreciate you all. Bye Now Im cancelling my account because I have wasted my entire day with this.

---

### Post by ugm6hr on 2008-02-09
@waterripples:
If you don't have the patience to read through the earlier posts, and compare 2 pieces of text, and report back, then you are probably not going to do well with Linux.

Because there are few people who know about Linux, you have to get help from forums (rather than people you know personally).

It is impossible to tell you what to do without some information.  The fact that you are not prepared to provide that information means that if I was to tell you what I *suspect* is the easy solution, I might be leading you up the garden path.  I also asked you to explain how you connected in Windows - you haven't responded.

Hence you **must** look at the output from your *lshw -C network* and compare it to mine, before I proceed.  You are only interested in about 3 words from the output at this stage - in the section under "Wireless"

If you decide to return to the familiar world of Windows - good luck.

---

### Post by waterripples on 2008-02-09
hahaha now im really laughing i cant even figure out how to cancel my account! lol what a day

---

### Post by ugm6hr on 2008-02-09
> **waterripples said:**
> hahaha now im really laughing i cant even figure out how to cancel my account! lol what a day

Since you are still here - have you tried left-clicking on the icon in the top right that looks like 2 computers (or possibly like 4 vertical grey bars)?

---

### Post by waterripples on 2008-02-09
Well, I remember it as Network, correct? I do remember left clicking it like i would any window. Left click selects what you highlight. So yes, I am pretty certain that I did. I don't recall right clicking it ever. As for gray bars Im not sure I dont have Unbuntu up right now. I had to return to windows so I can get some research. That's pretty much in a nutshell all I do is constant research so it is difficult to have to go back and forth. I don't understand either way whats causing the issue. If I knew what utilities I needed would solve the issue, I would tinker around but I have been all through network and tried everything to set it up. It just does not seem like the options the websites are running are not the same or maybe an outdated program. I have version 5.1 i think, is there a later version I may need?

---

### Post by waterripples on 2008-02-09
I am willing to paypal anyone $20 if they lead me to the resolution of my issue! LOL It has to be someone who will call me on the phone and tell me step by step by asking what I see. We can do it in less than 10 minutes if you can give good direction. LOL Think it's a joke? Ha

---

### Post by nynoah on 2008-02-09
I may not be understanding what you mean.  But when you say you have version 5.1......do you mean Ubuntu version 5.1?

---

### Post by nynoah on 2008-02-09
If you are using Ubuntu version 5.1  That is a VERY old version.  The code name for it was Breezy Badger.  We are now on version 7.10 Gutsy Gibbon.

Did you download Ubuntu from the net yourself and burn it on a disk, or did you get an Ubuntu CD given to you?

---

### Post by ugm6hr on 2008-02-09
> **waterripples said:**
> I dont see two computers on top of the other or where is this notification tab?>

Sorry.  I missed this important bit when I joined last time.

If you do not see this icon - you cannot be running an up-to-date Ubuntu.

Get Ubuntu 7.10 from here: [http://ubuntu.com/getubuntu/download](http://ubuntu.com/getubuntu/download)

This explains how to burn the CD: [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso)

---

### Post by nynoah on 2008-02-09
Can I make a suggestion, if you are going to be using the live cd all the time,  I suggest you get Linux Mint.  It is a version of Ubuntu Linux that contains all the codecs to do Flash and MP3s and other things like that.

Just do a search for linux mint on the net and then download the Gnome version.

Noah

---

### Post by JROQuinn on 2008-02-10
> **ugm6hr said:**
> Since you are still here - have you tried left-clicking on the icon in the top right that looks like 2 computers (or possibly like 4 vertical grey bars)?

Duh... that answered my problem. But yea I had Ubuntu 5.something when I came out & with my lappy, I gave up quick...install the new version, it should fix your problem as it did mine. Thanks guys. 

I can see how this can be frustrating. Just be patient. Im just amazed at how calm & how hard everyone tried to resolve this. Im looking forward to this community. Because Im gonna need everyone's patience too :p

---

### Post by waterripples on 2008-02-10
ok here is what I wish to accomplish. I want to be able to use Ubuntu for the internet so I can fully destroy windows on my hard drive. I want to cease using the live version where i use the disk and fully install ubuntu on my hard drive. I never ever want to go back to windows. So in short i want to graduate by getting online with ubuntu, knowing i can do it, then only then can i delete windows and fully install ubuntu

---

