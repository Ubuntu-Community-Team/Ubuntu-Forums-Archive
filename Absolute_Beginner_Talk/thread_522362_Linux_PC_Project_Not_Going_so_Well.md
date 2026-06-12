---
title: "Linux PC Project Not Going so Well"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by wasing on 2007-08-10
[SIZE="2"]well the computer im building was suppose to be my first built and first linux PC but i cant even get it to post...

I have all my Cables Connected to the right ports and spots
fans connectors in the correct places 
i turn on the computer and the fans spin for about 3 seconds and then stop until one day i decided to turn it on without the CPU in the socket...
everything works i can hear the harddrive spinning i can open my disk tray and my floppy LED is Green and working.. i replaced a faulty heatsink fan thinking it was shorting out causing it not to boot... but that wasn't it so then after i found that everything was working i thought that maybe i video card may have posted something but i didn't so i reseated it multiple times as well as my memory but still i could not get my PC to post anything so then i put the cpu back in to see if it would work and all that happened was my fans spun for 3 secs and the quit and the hardisk and CD did not even start...so i thought it was a problem with my CPU so then i went over to my friends to test the CPU and it Works fine... im really confused... also there is no beeping from the bios... and i also flashed the BIOS/CMOS with the jumpers and tested the battery...

i am so confused please help me 

Edit: i also tryed to boot my PC without the video card and ethernet card but that did not work either same problem occured  [/SIZE]

---

### Post by pointone on 2007-08-10
May be the power supply. Try testing with another one.

---

### Post by kast on 2007-08-10
Ok i have seen this before with my brothers computer, he sent it to me to fix and what it turned out to be (His issue) was he put in a new Power Supply and had plugged in one of the 4 prong power plugs to the MoBo but it was the wrong one. There was at least 4 different plugs  and a few different voltages and he had the wrong voltage plugged in

when he started it the fan would do like two spins then nothing, so i locate another cable (four prong) and switched it out and the pc came back up. not sure if this is your issue but wanted to share my experience.

---

### Post by forestpixie on 2007-08-10
I recently had a mobo with an 8pin ATX12v - which was new to me - it worked with the normal 4 pin if you plugged it into the right 4 pins

---

### Post by SeanTater on 2007-08-10
My motherboard did the same except the fans keep spinning, and it was a dead on arrival motherboard. In my case, I could plug the fans into either the power supply or the motherboard. If you can do that, try to connect it to the power supply  and see if it keeps running, if it doesn't then there is a good chance it's the power supply. If it does, then it's the motherboard..

---

### Post by kast on 2007-08-10
Oh i have also seen a user bring me her home built pc that did the same thing, it ended up being that he never put the spacers on the case to keep the MoBo from touch   :)

---

### Post by wasing on 2007-08-10
aw i knew i forgot to add something... anyway its quite an old MoBo its an Aopen MK33 Motherboard which had only a 20 pin Power Connector and the PSU had a 20 pin plus removable 4 pin connector so i could use my older mobos. is it possible that i need the exta for pins to power the  proccesor or complete the circuit if so i dont know where i would plug it in. it only has a twenty pin connector? im pretty sure it works because it powers my HDD, Floppy and CD-Drive.. as well as the Heat sink fan and Secondary fan which is connected to the motherboard itself... also aopen doesn't seem to keep allot of there older product information but this i all i could find on it 

[http://usa.aopen.com/products_detail.aspx?auno=219]("http://usa.aopen.com/products_detail.aspx?auno=219")

---

### Post by wasing on 2007-08-10
Spacers you mean like a washer...

is it possible its shorting with the case what do i use washers ?

---

### Post by oilchangeguy on 2007-08-10
does it have pci express? if so do you have it hooked up correctly. and no, if you don't have a 24 pin mobo, there's no other use for the extra 4 pin connector.

---

### Post by oilchangeguy on 2007-08-10
> **wasing said:**
> Spacers you mean like a washer...

is it possible its shorting with the case what do i use washers ?

no, you need to use standoffs. these can be found at any computer shop.

---

### Post by kast on 2007-08-10
When you buy a case they come with it, and some cases just have beveled circles that act like little risers to keep the Mobo off the case. sorry not that great of a description. if you put in the mobo in you would have had to screw these in, or you will notice that where the mobo screws into the case they are higher then the rest of the board.

---

### Post by wasing on 2007-08-10
ok my mobo has like a metallic circle around the screwholes but i also have what i think are standoffs that came with my case.. (they look like screws but the tops have screw threads in them) but i think i may have a MObo or CPU Socket Problem which mens a new Mobo anyway... this is my second mobo thought.. i would just get a better mobo and proccesor but i already bought a gig of PC133 Ram... :(:(:(:(

---

### Post by wasing on 2007-08-10
do standoffs go below or above the mobo i think its below the mobo but i just wanted to double check

---

### Post by Alterax on 2007-08-10
Since you and your friend have similar-socketed CPUs, here is what I recommend:

Try taking the computer to your friend's, and use your friend's CPU in your motherboard, case and all.  If the processors have some differences, this is all the better.

I had a similar situation where my father had given me a socket-370 pentium III a few years back to replace my socket-370 celeron.  Although the voltages were the same and the pins matched up perfectly, the motherboard that I had would not recognize the new processor.  Worked fine on my ex-wife's PC though.

Give this a try; if it boots fine, you may just need a different processor; your motherboard may just not be compatible with that one in particular.

--Alterax

---

### Post by kast on 2007-08-10
Yes there should be a washer looking circle around the screws holes, do they look like there bumped up? sitting higher then the rest of the board?

---

### Post by oilchangeguy on 2007-08-10
> **wasing said:**
> do standoffs go below or above the mobo i think its below the mobo but i just wanted to double check

i'm guessing this your first build, right? they go below.

---

### Post by Alterax on 2007-08-10
Standoffs go beneath the motherboard, but from your previous posts, your case already has those.

I don't think it is a shorting issue because you do get a different type of behavior when trying to run without a CPU and trying to run it with one.

Your problem is most likely the MOBO itself; either it is faulty or is incompatible with your processor, given the information from your previous posts.

Keep us posted.

--A

---

### Post by logos34 on 2007-08-10
> **wasing said:**
> but i already bought a gig of PC133 Ram... :(:(:(:(

Sounds like you're saying you just bought two 512MB sticks of pc133 ram, that may (also) be the problem...even though you say you're not getting any bios error beep codes.  The MK33 board specs says:

Support : PC133 SDRAM
Support ECC
DIMM : SDRAM DIMM
DIMM Type : 8/16/32/64/128/256MB
Max Memory : 1.5GB

i.e. max module size=256MB (although that doesn't seem to square that with '1.5GB'  max memory)

Then again maybe you're testing it with the existing ram, in which case the problem is something else, like unsupported processor model (as suggested above) or standoffs or bad power supply

---

### Post by oilchangeguy on 2007-08-10
> **logos34 said:**
> Sounds like you're saying you just bought two 512MB sticks of pc133 ram, that may (also) be the problem...even though you say you're not getting any bios error beep codes.  The MK33 board specs says:

Support : PC133 SDRAM
Support ECC
DIMM : SDRAM DIMM
DIMM Type : 8/16/32/64/128/256MB
Max Memory : 1.5GB

i.e. max module size=256MB (although that doesn't seem to square that with '1.5GB'  max memory)

Then again maybe you're testing it with the existing ram, in which case the problem is something else, like unsupported processor model (as suggested above) or standoffs or bad power supply

if the max ram is 1.5gb, then surely the motherboard has 3 slots. 512x3=1.5gb.

---

### Post by logos34 on 2007-08-10
> if the max ram is 1.5gb, then surely the motherboard has 3 slots. 512x3=1.5gb.

the specs say
DIMM Type : 8/16/32/64/128/**256MB**
Max Memory : 1.5GB

so 256x3=768MB

if the webpage for that board is correct then you won't be able to use ram sticks larger than 256MB.

---

### Post by wasing on 2007-08-11
Bump is still have not solved my problem i compared Proccesors with my Friends and they are both athlon thunderbirds which i checked and they are supported by my mobo so i think i may have to get a new mobo even thought i think it works... if anyone else had this issue and solved it please let me know

---

### Post by wasing on 2007-08-11
kk i replaced the mobo and it works... now one more problem thought... it wont post i think its the video card but if it was the video card wouldn't my bios be beeping... ive been hitting problems at every turn.. but im not turning back anyway to test and see if its the video card or if the AGP slot is busted.... ?

if you know any other posts that relate to mine please link them on this thread 

thank  you all for your help... you guys rock

---

### Post by kast on 2007-08-11
Does your new Mobo have a integrated graphics? just wondering for testing purposes.

---

### Post by wasing on 2007-08-11
naw as i said i had to get the same mobo so i could use the PC133 Memory so its still an MK33 and it didn't come with an intergrated graphics card... im really temped to take the graphics card out of this machine but im afraid its gonna get fried and its no longer under manufacturer warrenty so i dont really want to test it bucause then i cant replace it... its a rather old graphics card im using in the comp i am building (ATI 3D RAGE) so it may have been dead when i got it... (Got it from a IT guy i know who had some sitting in his basement and gave it to me for free)

Thanks again for all of your help earlier to..

---

### Post by kast on 2007-08-11
well lets run some of this down 

  ** 1.** another new mobo - works
  ** 2.** CPU tested in another pc works?
  ** 3.** memory is that new also?
  ** 4.** getting power, not the PS.
  ** 5.** received an old video card from a guy that had one kicking around his basement :)
  ** 6.** pc doesn't even come up with post

                     I'm leaning towards the video. does anyone have a video card you can just use to test? That or your monitor?

---

