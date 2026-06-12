---
title: "[SOLVED] Can't see my computer on the network"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by SteveHoffmanUK on 2008-03-17
This is probably a simple problem but I can't find the answer to it.

I have three machines on a wireless network:
1. Ubuntu Gutsy desktop
2. Ubuntu Dapper laptop
3. Windows XP desktop

They can all access the Internet via the wireless router, but none of them can "see" each other on the network. What do I need to do to be able to access the machines from each other?.

---

### Post by newlinux on 2008-03-17
When you say that can see each other can you be more specific (That can mean a few different things). Do you mean they can't ping each other or you can't access network shares or...

---

### Post by SteveHoffmanUK on 2008-03-17
Sorry I wasn't specific enough.

On the Ubuntu machines, when I go to Places > Network > Windows Network, nothing shows when I double-click on Windows Network icon.

Tried to ping, but not sure what Network address I should use. I tried 192.168.0.2 but it didn't return anything.

Does that help?

---

### Post by newlinux on 2008-03-17
I guess first steps first, lets verify you can ping each computer. find out the ip address of each computer (on ubuntu you can do this via commandline with the "ifconfig" command and on windows with the ipconfig command, or for both you can look in your network settings) and make sure you can ping each ip address. If that works, it is probably a network configuration issue.

do you have any network shares setup on any of the computers?

---

### Post by SteveHoffmanUK on 2008-03-17
Newlinux: thanks for trying to help. I'm not savvy about networking, but here goes...

Newlinux wrote:
> I guess first steps first, lets verify you can ping each computer. find out the ip address of each computer (on ubuntu you can do this via commandline with the "ifconfig" command and on windows with the ipconfig command, or for both you can look in your network settings) and make sure you can ping each ip address. If that works, it is probably a network configuration issue.

Found the ip addresses for the two Ubuntu machines (192.168.0.3 and 192.168.0.4) and got each to ping each other OK. I entered ipconfig into the 'Run' command line of my XP machine, the white-on-black window opened up a bit but then disappeared, so I don't know the ip address of the XP machine. Maybe we can just concentrate on the two Ubuntus for the moment.

>  do you have any network shares setup on any of the computers?

I have smbclient installed: how do I find if I have any shares set up?

I warned you that I don't know much about networking! :)

---

### Post by halitech on 2008-03-17
windows - Start Run - CMD

then type in ```
ipconfig
```

---

### Post by Black Hawk on 2008-03-17
To be able to see the ubuntu machines in the windows (smb) network, samba server (smbd) must be installed and running on both of the ubuntu machines!

---

### Post by SteveHoffmanUK on 2008-03-17
Halitech wrote:
> windows - Start Run - CMD

then type in
Code:

ipconfig



That's exactly what I did, the white-on-black terminal window opened momentarily and then disappeared!

Thanks for your help.

---

### Post by halitech on 2008-03-17
you need to open the command prompt first by going to the start button, then run and type in CMD, then do the ipconfig

---

### Post by SteveHoffmanUK on 2008-03-17
Black Hawk wrote:
> To be able to see the ubuntu machines in the windows (smb) network, samba server (smbd) must be installed and running on both of the ubuntu machines!

Thanks for your help.

OK, I installed samba on my Ubuntu desktop (Machine 1 in my original message)
Then I entered 'smbd' in my terminal; came back with normal prompt, which I assume means that the samba server is running OK (is that right?). Then I looked for that machine in my Windows machine and can't see it still. :(

---

### Post by SteveHoffmanUK on 2008-03-17
AHA!

On my desktop (Machine 1) and my  laptop (Machine 2) I can now "see" (in Places > Network > Windows Network > MSHome) both Ubuntu machines, so that part of my problem has clearly been solved by installing and running Samba server.

Wa hay - making progress!

Now why can't I see the Ubuntu machines in Windoze?

---

### Post by newlinux on 2008-03-17
does your windows machine have any shares setup? If the cmd prompt isn't working, somewhere in your network settings (I'm not at a windows terminal right now) you should be able to find your windows IP address to ping. You can also open up the cmd prompt and try pinging your ubuntu machines from your windows machine.

---

### Post by SteveHoffmanUK on 2008-03-17
Hmmm...

Worrying development: I went to my XP machine and now discover that I can't access the Internet and it's complaining about poor connectivity and recommends that I repair my wireless connection. So I try to repair, but it fails in "renewing my IP address", whatever that means. It tells me to contact the person in charge of my network. Unfortunately, that's me!

I shall be in deep doo-doo, as this is my wife's machine. :(

The only thing I did on the Windows machine was to type that cmd in - ipconfig.

Any ideas? I realise that this isn't a Windoze forum, but nevertheless,I'm desperate.

---

### Post by roccity1 on 2008-03-17
when I set up my network i run 3 computers like you.I have a windows machine that is the main computer (because of my internet) and ubuntu and vector linux on the others.I found that if you go into the network manager setup and use a static ip address like the ones you have 192.168.0.3 and .4 I think you said they were.add your man machine as the gateway and as the dns.

so you should have something like this:

ip addy 192.168.0.3
netmask 255.255.255.0
gateway (the main machine)

dns (themain amchine) and any from your isp.

try that and see how ya go

---

### Post by SteveHoffmanUK on 2008-03-17
roccity:

Thanks for your help.

I don't want to have my XP machine (or any machine) to be my "main" machine and my gateway to the Internet. If I do that, then I have to have that machine turned on when accessing the Internet from the other machines.

All three machines have always been able to access the Internet independently of one another - through the wireless router, and I want to keep that.

Why should my XP machine's network connection suddenly not work? It must have something to do with this messing about that I've just been doing.

---

### Post by SteveHoffmanUK on 2008-03-17
It's OK, 's OK!

I tried the usual Windoze technique (rocket science, this) of disconnecting and reconnecting to my wireless network, and now everything works on my XP machine.

Even better, I can now see my Ubuntu machines from my XP machine.

Thanks to everyone here for their swift and wise help.

Problem solved!:)

---

