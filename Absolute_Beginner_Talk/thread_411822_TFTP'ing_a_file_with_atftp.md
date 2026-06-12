---
title: "TFTP'ing a file with atftp"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by madmalice on 2007-04-17
When trying to tftp a file to my router (wrt54gs v.6) from the terminal command line in ATFTP I get a source port mismatch, how can I sync my ports between the router and the computer so that they can transfer the file? I set my network to a static ip address(192.168.1.99) and tried connecting it at a specific port(69) as well as using 192.168.1.1. So my commands are as follows:

tftp>connect 192.168.1.99 [69]
tftp>mode netascii
tftp>trace
tftp>put (firmware_filename) 192.168.1.99

or the same as above with 192.168.1.1

1) do I need to use a different method/program of tftp'ing so I can do a binary transfer?
2) how do I sync my ports/set my ip address properly to a static address if it not via applications>system>networking>properties

if I use the address above (192.168.1.99) it says it is sent but the router does not receive it that way, if I use 192.168.1.1 the default for the router it says sent wrq source port mismatch and then aborted. I am so proud of almost figuring it out on my own only to get stumped because they arent using the same port, sigh. Well for a newbie I was close, I have seen the tutorials on what I am trying to do although there isnt much out there for tftp'ing a file unfortunately so I am asking for a little advice. Anyone who has any idea what I can do to send my router the firmware file since my router is sitting midflash waiting for the upload you could be a lifesaver and thanks sincerely for any advice, otherwise I may have a paperweight sale in the near future!

:KS

---

### Post by lamalex on 2007-04-17
i just use tftp to send files to my router, and i don't change the ports. i do this
```
sudo apt-get install tftp
tftp 192.168.11.1
binary
trace
rexmt 1
put filename.trx

```

are you doing openwrt?
also as far as the static, what i've found that I've needed to do is put a switch between me and the router to keep my computer connection alive

---

### Post by madmalice on 2007-04-17
dd-wrt, I have already loaded the killer and prep .bin files via the web interface, all that is left is to send it the dd-wrt.v23_micro_generic.bin file. so why do I need to use 192.168.11.1, that is just a curiosity question as I thought it needed to go to 192.168.1.1

---

### Post by lamalex on 2007-04-17
have you sent the others via tftp? if yes what did you change in your procedure?

---

### Post by madmalice on 2007-04-17
No I did not send them via tftp, I basically used the instructions listed here:

Download [vxworks_prep_gs_v03.zip] and extract. 

Download and extract [vxworks_killer_gs_v08.zip], OR create a custom firmware image with your MAC address embedded in it. See the 'Changing your MAC address' section below for more information. 

Download [DD-WRT micro generic]. You may want to check [DD-WRT] to make sure there isn't a newer version than v23 SP1. Do not use the one labelled 'WRT54G' or 'WRT54GS', use the 'generic' version. 

If you don't know how to use (or don't have) a console mode TFTP tool (i.e. tftp.exe), download the [Linksys TFTP transfer tool]. 

You will want to assign your network adaptor a manual IP address, since you may loose your automatically configured one and have trouble TFTP'ing the firmware. To do this see the troubleshooting section or google it. It's done at the properties dialog of your network connection, in the 'Internet Protocol (TCP/IP)' properties. 

Go to your router's web based interface and enter the 'Administration' tab. Then select 'Firmware Upgrade' and choose the vxworks_prep_gs_v03.bin file. Hit apply. After a minute, your browser window will go blank. At this point, power cycle your router. 

Again point your web browser to [http://192.168.1.1](http://192.168.1.1). You'll see a different sort of firmware upgrade screen. This is the Management Mode. Select and apply the vxworks_killer_gs_v08.bin firmware upgrade. WAIT for your browser window to turn to report 'Success'. Have troubles? Try a different web browser, the http daemon in management mode is very finicky. 

Now unplug the power cord of your router, then plug it back in. The power LED should now be blinking. 


:KS  (here is where I am at from there)


Now you need to do a binary mode TFTP transfer of DD-WRT micro generic to your router. To do this you can use the Windows TFTP console mode utility, the Linksys TFTP Windows GUI utility, or some other TFTP client. You may have to disable your firewall if by some chance it is blocking outgoing connections on port 69. Many TFTP clients don't default to binary mode, so be sure to specify it (i.e. the -i switch with the Windows console mode TFTP utility). 
For Windows TFTP console mode utility (example, adjust accordingly): 
tftp -i 192.168.1.1 put dd-wrt.v23_micro_generic.bin 
For the GUI utility 
simply enter your router's IP (192.168.1.1), select dd-wrt.v23_micro_generic.bin, leave the password field blank, and initiate the transfer. 

Do NOT reboot your router after TFTP'ing, this will happen automatically. It takes a couple minutes after the TFTP transfer finishes for the firmware to actually be flashed.

---

### Post by lamalex on 2007-04-17
ok this is how i do it, and I do it a lot because I make openwrt routers for clients at my work almost every day.

either set computer IP static in range of the router, for example if your router is 192.168.0.1 then make your computer 192.168.0.2 or keep your computer in dhcp and put a switch between you and the router, you need to keep your computer ethernet port active or else it will fail. Unplug the router's powrt and execute the following commands in terminal:
```

tftp 192.168.11.1
binary
trace
rexmt 1
put firmwarefile.bin

```
after put plug your router back in. there is a 3 second period after initial boot that it will accept tftp firmware transfers. you should see tons of text scroll by and your router should reboot into its new firmware congrats!

---

### Post by madmalice on 2007-04-17
So do I have a brick on my hands since I unplugged it once already and plugged it back in and my transfer didn't work, maybe I took to long? Oh no!!!! 

:)

---

### Post by madmalice on 2007-04-17
I shouldnt have a brick yet because only my power led is blinking and they arent solid across the board, solving this dilema is giving me new hope for using linux( I am a couple weeks into a linux only, a windows convert if you will). Plus good answers from people like yourself, thanks a lot man I really appreciate it a ton, hopefully someday I can help people out in return when I get to know this stuff better myself, this is all strictly hobby for me I am a boring guy who works a mundane warehouse job(bad life decisions, what can I say...), so my programming knowledge is limited to what I learn in my free time, teaching myself from the ground up so at least there a great community that you all have going here.

Thanks again,

Madmalice

---

### Post by lamalex on 2007-04-17
yikes! no you should be ok, at least I've  never bricked any of mine. keep trying tftp can be fickle, it took me a while to get it right.

---

### Post by madmalice on 2007-04-17
I will have to try everything unfortunately later this evening to see if it all goes cause I have to work now.... but I understood everything you are telling me and appreciate all your help once again, perhaps I will post I am alex is my hero tomorrow morning if everything goes well.

Sincerely,

Maddmalice

---

### Post by adamc55 on 2007-11-03
OK, I've been trying this with a Buffalo WHR-G54S and haven't had much luck. Maybe someone can give me a clue:

If I follow the standard instructions with TFTP, I get something like this:

```
tftp> binary
tftp> trace 
Packet tracing on.
tftp> rexmt 1
tftp> connect 192.168.11.1
tftp> put dd-wrt.v23_micro_generic.bin
sent WRQ <file=dd-wrt.v23_micro_generic.bin, mode=octet>
sent WRQ <file=dd-wrt.v23_micro_generic.bin, mode=octet>
sent WRQ <file=dd-wrt.v23_micro_generic.bin, mode=octet>
sent WRQ <file=dd-wrt.v23_micro_generic.bin, mode=octet>
sent WRQ <file=dd-wrt.v23_micro_generic.bin, mode=octet>
...
sent WRQ <file=dd-wrt.v23_micro_generic.bin, mode=octet>
Transfer timed out.

```

If I try atftp, I get something like this:
```
Verbose mode on.
tftp> trace
Trace mode on.
tftp> connect 192.168.11.1
tftp> put dd-wrt.v23_micro_generic.bin
sent WRQ <file: dd-wrt.v23_micro_generic.bin, mode: octet <>>
source port mismatch, check bypassedtimeout: retrying...
sent WRQ <file: dd-wrt.v23_micro_generic.bin, mode: octet <>>
source port mismatch, check bypassedtimeout: retrying...
sent WRQ <file: dd-wrt.v23_micro_generic.bin, mode: octet <>>
source port mismatch, check bypassedtimeout: retrying...
sent WRQ <file: dd-wrt.v23_micro_generic.bin, mode: octet <>>
source port mismatch, check bypassedtimeout: retrying...
sent WRQ <file: dd-wrt.v23_micro_generic.bin, mode: octet <>>
source port mismatch, check bypassedtftp: unknown error.
tftp: aborting

```

The good news is that I do not appear to have bricked the WHR-G54S. The bad news is I haven't made any progress toward dd-wrt, either.

---

### Post by Billy_McBong on 2007-12-08
i have the exact same problem as adamc55
anyone have any advice?

---

### Post by redman5087 on 2008-03-11
Same problem with Linksys wag354g
atftp and tftp, same errors messages

any help would be appreciated

---

