---
title: "How to edit the INI file in a Ventrilo server"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by PotatoMasher on 2007-09-26
Hello everybody!
I wanted to know more about editing the INI file in the Ventrilo server installation directory. I know how to open and editing it but I don't know how to properly set up all those magnificent options.

I found this:

on the official website of ventrilo, but they are not very precise about BY WHAT replacing the default options.

Let's start by the phonetic name of the server. Anyone having any basis in phonetical alphabet knows how to write "Potato's server" in phonetic??8-[

Thanks for your attention and your potential help on any eventually of modifying an option f the INI linked above!

---

### Post by wheredidrealitygo on 2007-09-26
You didn't post any links ;)

is it possible for you to post the entire contents of the .ini file so we can see all the options?

---

### Post by PotatoMasher on 2007-09-27
Uhhhh!
Sorry, I tried to post a link and it did'nt work (You'll see, when I'll get used to this forum, I wont do these errors!)

So, as I were saying (or writing, depending on the point of view):
Here is the content of the INI file I am trying to customize:
_______________________________
[Server]

Name=Server 1
Phonetic=Server 1
Port=3784
Auth=0
Duplicates=1
AdminPassword=
Password=
MaxClients=8
SendBuffer=0
RecvBuffer=0
Diag=0
LogonTimeout=5
CloseStd=1
TimeStamp=0
PingRate=10
ExtraBuffer=0
ChanWidth=0
ChanDepth=0
ChanClients=0
DisableQuit=1
VoiceCodec=0
VoiceFormat=1
SilentLobby=0
AutoKick=0

[Intf]

# Examples:
#
# Intf=192.168.0.30
# Intf=external.mydomain.com
# Intf=internal.mydomain.com
# Intf=127.0.0.1
________________________________

This file is kinda made for the people like me, they give information on the usefullness of each line in a  "too-long-to-post" htm file that I have linked below:
[https://ventrilo.mycp.net/docs/ventrilo_srv.htm](https://ventrilo.mycp.net/docs/ventrilo_srv.htm)

But I still have few little problems. Ok, I know what to put in the Admin password area, in the Password area (which defines what is the password required to connect to my server) and in the Server Name area.=D>

Still, I don't know how to phonetically write my server's name, nor how to connect to my server from my other computer (if necessary, I can make a new specific thread for this!). If anyone finds anything on how to translate "Potato's server" to phonetic language, please post.

Thanks for your replies!!
:popcorn:

---

### Post by wheredidrealitygo on 2007-09-28
(english after)

Laissez moi savoir si t'as besoin ce poste en français.

About the phonetics, I have no clue, but in order for other people that are not on your network to connect to your server, you must do a few things:

1. forward port 3784 from your router to the ip of that particular server.

usually this involves logging into the router (in my case, 192.168.2.1), and specifying that it points port 3784 to the IP of that server (for my example, I have comptuer A at 192.168.2.20, and Server A at 192.168.2.70). Those are internal, network-only IP's. Your router will have it's own IP. You would port forward 3784 to the IP of your router (in my case, to 192.168.2.70). that way, when someone goes to the IP of your router, this particular ventrilo server request will go to the computer with the ventrilo server on it.

2. unblock port 3784 on your firewall (if you have one)

3. set up a dynamic dns updating client on the server.

i use no-ip.com, they have a good walkthrough (posted [here]("http://www.no-ip.com/support/guides/update_clients/setting_up_linux_update_client.html")) on how to set up dynamic dns on a linux box. this is so instead of having to type an IP address, you get a fake-ish domain name that will constantly point to your server. for example, if you wanted it to be ventriloserver.bounceme.net (other domains are available), the dynamic dns client would point it to your ip, that way you can give someone this domain, and not have to tell them your IP every time it changes.

4. use a ventrilo client (installed on someone elses computer, not on your network) to test that everything works. for the server, type in the dynamically updated dns (so from our example, ventriloserver.bounceme.net), this will go through the update client to your server, and the router will forward the request (along port 3784) to your server, and it should (and did with me) instantly connect. it may ask for the password if you've set one.

Voilà Ventrilo access :D

---

### Post by PotatoMasher on 2007-09-28
Thanks a lot!
Those infos will be very useful and I will try to have my server up and running during the week-end.

And thanks for the proposition of a french version of your post (you too speak french??), but I am equally familiar with both languages and I prefer the technic terms in english (they are more precise)!

---

