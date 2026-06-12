---
title: "i'm installed ubuntu but i dont no how to connect to the internet"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by gayanhewa on 2006-11-22
HEllo ppl 
  Im a total new 2 linux i have installed ubuntu 6.06 on my laptop latitude c810 .. ( ya it's a bit old) .. But i don't no how to connect to the internet .. I have  ADSL connection and a dlink router with 4 ports py other pc is connected to the router it has windows and its working .. So i don't want to continue with windows so i need to configure the Internet connection fast .. 

Is there any way to configure adsl automatically .. I tried using pppoeconf but it say i am already using it ... 

G**_ayan _**

---

### Post by moephan on 2006-11-22
Have you used the network utility? 
Use the main menus to go: System->Administration->Networking.

Cheers, Rick

---

### Post by ciscosurfer on 2006-11-22
Welcome gayanhewa!

Check [out this link and see if that helps]("https://help.ubuntu.com/community/ADSLPPPoE") :-)

---

### Post by gayanhewa on 2006-11-23
> **ciscosurfer said:**
> Welcome gayanhewa!

Check [out this link and see if that helps]("https://help.ubuntu.com/community/ADSLPPPoE") :-)
hey ppl .. my network is OK becaouse .. i can access my windows shares freom the network only the internet won't configure .. 

i used pppoeconf but it says that im using it already .. 

 Save me !!!

---

### Post by kiyometane on 2006-11-23
if you've already configure your eth0, go to terminal and type in 
" sudo dhclient " one, 2 or 3 times until u get the connection.

---

### Post by timothy_duncan on 2006-11-24
hi all,

i thought ill just add up to this post instead of opening a new one with the same problem.  i managed to install kubuntu 6.06 on an old box.  it's a PIII 550MHz, 512kRAM.  i can't configure the internet to work.  it seems that the ethernet card is not being detected.  i tried the process given above (using pppoeconf) it says that there is no ethernet detected and will try to detect it again but it still can't be detected.  my ethernet card is a plug n play ethernet card.  im just a newbie on everything so i really need any help that you could give..  

cheers

---

### Post by Bachstelze on 2006-11-24
Please give more details about your card. Th output of *lspci* might help.

---

### Post by timothy_duncan on 2006-11-24
> **HymnToLife said:**
> Please give more details about your card. Th output of *lspci* might help.

uhmmm...  how would i do that?  please bear with me as i dont know anything about linux.  would you could please outline the steps that i need to do :oops: 

TIA

---

### Post by Bachstelze on 2006-11-24
Just open up a [terminal](http://psychocats.net/ubuntu/terminal), type *lspci* and copy/paste what you get :)

---

### Post by Sef on 2006-11-24
Applications > Accessories > Terminal

type  lspci and then enter

---

### Post by timothy_duncan on 2006-11-24
here is it:

0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host Bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP Bridge (rev 03)
0000:00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
0000:00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
0000:01:00.0 VGA Compatible controller: Silicon Integrated System [SiS] 86C326
5598/6326 (rev d2)

thanks in advance again!

---

### Post by timothy_duncan on 2006-11-24
any takers please..

---

### Post by jamesr on 2006-11-24
Hi,

I do not see a nic in the list whereas earlier I thought you had stated that the network was seen.

Try the following, go to the terminal again and enter ```
dmesg |grep eth0
``` and post the output.

Also what is the NIC? is it ISA or PCI?

---

### Post by timothy_duncan on 2006-11-24
```
dmesg |grep eth0
```
i tried it but got no results.  i just tried dmesg and it outputs heaps of messages..  it seems that my ethernet card is not being detected..  i really dont know if the card is working or not but when i hooked up the cable from my adsl modem, the leds are all flashing up.  btw, my modem is a dlink dsl-302g.  

the NIC is ISA, inserted in the black connector..

---

### Post by jamesr on 2006-11-24
Hi,

I need to know the NIC type because it looks as if you will have have to ```
sudo modprobe xxxxx
```where xxxxx is the type of NIC to find the NIC. This is only the testing phase but we should be able to set it up automatically  if we can get it to work manually.

---

### Post by timothy_duncan on 2006-11-25
i dont know what im doing wrong but i did
```
dmesg |grep eth0
``` and got no results..  ](*,)

---

### Post by houstonbofh on 2006-11-25
Well, you are correct in that Ubuntu is not seeing your NIC.  lspci is a command to LIst PCI devices in your system.  Since the card is ISA, that won't work.  modprobe will, but it is more like yelling "Hey Bob" into a dark room.  The thing is, we have to know Bob's name first.  You will need to post the NIC type here, or you can grab a pci nic somewhere.

---

### Post by timothy_duncan on 2006-11-26
> **jamesr said:**
> Hi,

I need to know the NIC type because it looks as if you will have have to ```
sudo modprobe xxxxx
```where xxxxx is the type of NIC to find the NIC. This is only the testing phase but we should be able to set it up automatically  if we can get it to work manually.

since it's an ISA, do i do 
```
sudo modprobe ISA
```

or do i have to put in the NIC's name, which i dont have an idea.  sorry i'm a newbie in linux and though i've been using computer, i really didn't have an idea with regards to hardware.  when i boot up my pc, all it says with regards to the NIC is it is a Plug n Play Ethernet card.. 

thanks for your response.. would appreciate any help out there to get my internet connection working..  cheers!

---

### Post by houstonbofh on 2006-11-26
> **timothy_duncan said:**
> or do i have to put in the NIC's name, which i dont have an idea.  sorry i'm a newbie in linux and though i've been using computer, i really didn't have an idea with regards to hardware.  when i boot up my pc, all it says with regards to the NIC is it is a Plug n Play Ethernet card.. 

thanks for your response.. would appreciate any help out there to get my internet connection working..  cheers!
You need to open the case and look at the card.  There is no way to find it from the OS, and that is why the drivers are not installed.

---

### Post by david_kt on 2006-11-27
May be you need to install NTLMAPS
================================================================
[http://packages.ubuntulinux.org/dapper/web/ntlmaps](http://packages.ubuntulinux.org/dapper/web/ntlmaps)
'NTLM Authorization Proxy Server' (APS) is a proxy software that allows you to authenticate via an MS Proxy Server (e.g. ISA server) using the proprietary NTLM protocol. Since version 0.9.5 APS has an ability to behave as a standalone proxy server and authenticate http clients at web servers using NTLM method. It can change arbitrary values in your client's request header so that those requests will look like they were created by MS IE. It is written in Python v1.5.2 language.
=================================================================

You should enable universe repositary first in order to install it using sypnatic manager. Otherwise use terminal:

sudo apt-get install ntlmaps.

Regards,
DK

---

### Post by jamesr on 2006-11-29
Hi David_kt,

The software additions refers to the ISA (microsoft FUD) server, cannot remember what ISA stands for in this case but it definately does not refer to an ISA card. 

Hi gayanhewa or timothy_duncan,
Just open the case, and  supply us with the board number or name. It usually printed on the board somewhere or you could supply the FCCID number, then we could go forward. A lot of the older ISA card need to be manually IDed because PCI cards are more common now. All of my older systems have ISA NICs are they are fast enough for internet browsing etc.

---

### Post by timothy_duncan on 2006-11-30
i opened my old box and took out the NIC, printed in the PCB is **PLANET** (in big capital letters, thus i assume it is the name of the card) and next line says, **Plug and Play Ethernet Card**.  

there's no FCCID anywhere, but there's a print saying "Complies with FCC Class A".  At the back, there's a bar code with this printed "**ENW-2400P-2T(V.2) *9602546***"

thanks for the replies guys!  I'm really frustrated and was thinking of shelving linux for a while.  but  i guess, with guys like you trying to reach out and when out of your way to help newbies, i think the least  that i could do is try to supply you with much info as possible..

---

### Post by jamesr on 2006-11-30
Hi, 

I have found somebody in Finland with one of these cards. I should be getting a reply giving the modprobe code.

It is a Mayfield NIC , European.

---

### Post by Bartender on 2006-11-30
timothy -
Do you have any vacant PCI slots, and do you reside anywhere near civilization?  PCI NIC's are a dime a dozen.  Any PC salvage or repair shop oughta have a box full.  
Wouldn't that be much easier than screwing around with some ancient ISA NIC?

---

### Post by david_kt on 2006-12-04
[QUOTE=jamesr;1825372]Hi David_kt,

The software additions refers to the ISA (microsoft FUD) server, cannot remember what ISA stands for in this case but it definately does not refer to an ISA card. 

Hi James,
I don't think there is a problem in the card as he said he could access windows share files:
================================================================
i can access my windows shares freom the network only the internet won't configure ..

i used pppoeconf but it says that im using it already .. 
================================================================

If he could not access network at all, then, the problem could be with network card driver but looks like this is not the case.

I have similar situation before, i.e I could access all network resources, except internet access which is governed using MS ISA (Microsoft's Internet Security and Acceleration Server).

The problem is that MS ISA do not response to firefox, or put it another way: firefox does not know how to request access. MS ISA could talk to Microsoft internet explorer only so far.

Using NTLMAPS, firefox would be able to authenticate itself through MS ISA.

Regards,
DK

---

### Post by jofobuntu on 2006-12-05
OK, this ISA/ntlmaps thing is killing me.  I've setup ntlmaps and used both the http_proxy environment variable and the apt.conf to point to the proxy.  The programs seem to be using the proxy but I am still getting 307 temporary redirects.

When I use firefox, I can surf the web. Also, I can even use wget manually and it will work.  But when I use apt-get, all I get are failures.  What's more is that right next to this machine is my debian box which works flawlessyly but I have not been able to determine the key difference between the two.

Have I overlooked something?  Please help!

---

### Post by compmodder26 on 2006-12-05
> **david_kt said:**
> [QUOTE=jamesr;1825372]Hi David_kt,

The software additions refers to the ISA (microsoft FUD) server, cannot remember what ISA stands for in this case but it definately does not refer to an ISA card. 

Hi James,
I don't think there is a problem in the card as he said he could access windows share files:
================================================================
i can access my windows shares freom the network only the internet won't configure ..

i used pppoeconf but it says that im using it already .. 
================================================================

If he could not access network at all, then, the problem could be with network card driver but looks like this is not the case.

I have similar situation before, i.e I could access all network resources, except internet access which is governed using MS ISA (Microsoft's Internet Security and Acceleration Server).

The problem is that MS ISA do not response to firefox, or put it another way: firefox does not know how to request access. MS ISA could talk to Microsoft internet explorer only so far.

Using NTLMAPS, firefox would be able to authenticate itself through MS ISA.

Regards,
DK

This is the problem that occurs when two people post their problems in the same thread.  James was thinking you were replying in regards to timothy_duncan when you were really replying to gayanhewa.

---

### Post by david_kt on 2006-12-05
> **jofobuntu said:**
> 
When I use firefox, I can surf the web. Also, I can even use wget manually and it will work.  But when I use apt-get, all I get are failures.  What's more is that right next to this machine is my debian box which works flawlessyly but I have not been able to determine the key difference between the two.

Have I overlooked something?  Please help!

Jofo,
You should post here what kind of program you are trying to install and what kind of error you are receiving. Otherwise, I could only guess your problem. Anyhow, let me guess your problem:
1. The server hosting the program you are trying to install are having temporary problem
Solution: Try it again or try it other time or change server, but looks like this is not the case as you said that your debian box is working well. Then, this lead us to next possible problem:

2. The server hosting your program is not in your source list. To add this, please add repository to include universe and multiverse. And you could add the server manually as well using sypnatic manager. Or, you could edit source.list using
sudo gedit etc/apt/source.list
And add whatever server hosting the program.

3. The debian packeges you are trying to install is not supported by Ubuntu. In this case, it is better to compile the program from the source code. Download the source code, and then install it using:

./configure
make
sudo make install

from the directory of the source code.
When you do ./configure, please observe whatever error/instruction come out, you might need to install additional program and repeat ./configure, until there is no error. Please check also ./configure --help to see any additional command to include. If you need to enable something, do again:

./configure --abcdef (additional command, may be more than one).

After you satisfy with it, then, do make and sudo make install.

Regards,
DK

---

