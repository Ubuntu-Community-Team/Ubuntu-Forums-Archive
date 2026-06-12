---
title: "azureus HTML interface"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-07-06
I have been following a couple of guides that set up an Ubuntu computer as a dedicated torrent box using azureus and its HTML web interface plugin.  It's all working and now i'm just wondering if I can remotely download new torrents using the web interface and if so how do i do it.

Thanks in advance,

VC

---

### Post by videocheez on 2007-07-06
*bumP*

I know this question is somewhat linux azureus related but I figured somebody would who knows Ubuntu and azureus could help me out.

---

### Post by SlackLagg on 2007-07-08
Yes you can do that. After you have the webUI plugin installed and configured (I'm assuming you've done that already) you just click the "Upload" tag near the upper right hand corner (again assuming you are using on of the default CSS files ) 

After you've clicked upload you can copy N paste in a URL or upload a local file like you would an FTP.

---

### Post by videocheez on 2007-07-08
Thanks that worked out well.  Now i was wondering do you know how to password protect access to azureues ofver the web.  I would hate for some one to find the url of my server and upload some kiddie porn links.  

I just set up a dedicated ubuntu torrent box using azurreus and its web interface and I would like to enable password protection for the web interface portion so that not just anyone can access my azureus client. I saw the following commands but i don't understand what the word password means after mypassword. Any help would be appreciated. PS i know that this is not totally linux related but this is for an ubntu torrent box.

```

set Plugin.azhtmlwebui.User myusername
set Plugin.azhtmlwebui.Password mypassword password

```

---

### Post by SlackLagg on 2007-07-09
I'm not really sure about that. When I configured the plugin I did it with the Azureus client (IE it was GUI, just fill in the blank, and I'm assuming you're setting it up via terminal) 

If I had to take a guess I would say that "mypassword" is probably a typo and that it should instead read 

```

set Plugin.azhtmlwebui.Password myusername password

```

Do you have a link were you are getting that information, or is it comming up in a log or terminal or something ?

---

### Post by videocheez on 2007-07-09
> **SlackLagg said:**
> 

Do you have a link were you are getting that information, or is it comming up in a log or terminal or something ?

[http://geeksnotnerds.com/node/111](http://geeksnotnerds.com/node/111)

I saw the same thing at a few other locations but I can't remember URL's

---

### Post by SlackLagg on 2007-07-09
Ah , thanks for that link. I may have to convert my spar box into a torrent machine with this bit of information. Anyhow, I got it to work. 

I'll use Foo as a username and Bar for a password

goes like this

```

set Plugin.azhtmlwebui.User Foo
set Plugin.azhtmlwebui.Password Bar password

```

Apparently the word "password" is needed so that it will hash/encrypt/do something with the password instead of keep it as as string. (I tried without the "password" part and it didn't care much for my password when I tried to enter it)

EDIT:

I didn't look around too much, but from looking at the fill in the blank entries for the Plugin using a Azureus GUI, to limit the range of IP's that can access the box the command is

```

set Plugin.azhtmlwebui.Access foo

``` 

where foo can be:

"local"   (no quotes, but this is  for only local machine which is not every useful to you)
"all" (again, no quotes, but allows access from all IP's)
XXX.XXX.XXX.XXX  ( substitute your IP for x, and it will only all access from that IP number, pretty useful if you are going to only access it from work, etc)
XXX.XXX.XXX.XXX - XXX.XXX.XXX.YYY  ( this is for a range of IP's. This is probably what I would do, set for the range of IP's that my router makes, IE   192.168.1.01 - 192.168.1.100 )                     

If you change that (or pretty much any other setting for the plugin) you'll need to restart Azureus.

If you've already figured that out, I don't mean to insult you, It's just I didn't come across it on that link or any of the other ones I saw. If you want a full list of options for that plugin, I can put those down too.

---

### Post by videocheez on 2007-07-09
> **SlackLagg said:**
> Ah , thanks for that link. I may have to convert my spar box into a torrent machine with this bit of information. Anyhow, I got it to work. 

I'll use Foo as a username and Bar for a password

goes like this

```

set Plugin.azhtmlwebui.User Foo
set Plugin.azhtmlwebui.Password Bar password

```

Apparently the word "password" is needed so that it will hash/encrypt/do something with the password instead of keep it as as string. (I tried without the "password" part and it didn't care much for my password when I tried to enter it)

EDIT:

I didn't look around too much, but from looking at the fill in the blank entries for the Plugin using a Azureus GUI, to limit the range of IP's that can access the box the command is

```

set Plugin.azhtmlwebui.Access foo

``` 

where foo can be:

"local"   (no quotes, but this is  for only local machine which is not every useful to you)
"all" (again, no quotes, but allows access from all IP's)
XXX.XXX.XXX.XXX  ( substitute your IP for x, and it will only all access from that IP number, pretty useful if you are going to only access it from work, etc)
XXX.XXX.XXX.XXX - XXX.XXX.XXX.YYY  ( this is for a range of IP's. This is probably what I would do, set for the range of IP's that my router makes, IE   192.168.1.01 - 192.168.1.100 )                     

If you change that (or pretty much any other setting for the plugin) you'll need to restart Azureus.

If you've already figured that out, I don't mean to insult you, It's just I didn't come across it on that link or any of the other ones I saw. If you want a full list of options for that plugin, I can put those down too.

Thanks for the info.  You clarified the password thing.  The only problem is that it didn't work.  Where do I enter this info?  Do I open a terminal and enter the password code or is it entered into azureus somehow?

thx,

VC

---

### Post by SlackLagg on 2007-07-09
Once you run java -jar Azureus.jar  --ui=console or whatever the command is, Azureus will start running and after it's stopped whizzing text by (ie there will be a blank cursor, not like in bash were there is a prompt) you can enter it there, 

it's pretty detailed in that link you gave me, just follow that line by line. 

the jist of it is this:

open console

ssh to machine

screen "command to open azureus"

type in the set Plugin. blah blah blah commands

use browser to test.

---

### Post by videocheez on 2007-07-10
> **SlackLagg said:**
> Once you run java -jar Azureus.jar  --ui=console or whatever the command is, Azureus will start running and after it's stopped whizzing text by (ie there will be a blank cursor, not like in bash were there is a prompt) you can enter it there, 

it's pretty detailed in that link you gave me, just follow that line by line. 

the jist of it is this:

open console

ssh to machine

screen "command to open azureus"

type in the set Plugin. blah blah blah commands

use browser to test.

I suppose I shouldn't complain since I didn't follow the guide line for line.  I only took the parts that I liked.  i did not install screen yet, since I'm not interested in doing azureus from the command line.  Seems like too much work.  Once I learn all the commands and learn to type faster, maybe I'll see the benefit.  Anyways I poked around on the web further and found that the password for the web interface plugin can be added through the gui by going into tools-->options --> plugins --> HTML Web UI then scroll down to the button and enter a password.

thanks for your help.  Now it's time to tackle my next linux problem which is figuring out how to get a remote desktop form windows to linux and vice versa.

VC

---

