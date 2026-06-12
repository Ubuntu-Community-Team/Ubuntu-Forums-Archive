---
title: "BIOS not recognising CD/DVD drive"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by RedGreen on 2007-10-04
I am trying to get my PC to boot off of a Ubuntu 7.04 disc, I usually have no problems with booting from a CD although for some reason I cannot get this to work right. My BIOS (PHOENIX 5.1.39) does not recognize my drives. I have a DVD burner and a CD burner hooked up to the machine but the only option I get in the boot order screen is "cd drive" and setting it first in the order doesnt allow me to boot off the cd in either drive.

Any suggestions, I have been playing with settings for a while and cant find a way to get the BIOS to recognize my drives.

Thanks

---

### Post by w4ett on 2007-10-04
If you have both optical drives on the same channel, please check that your jumper settings are correct....one needs to be set as master and the other set as slave.   Then go into your bios and run the drive detect to re-establish communication to the drives on the channel

---

### Post by Pumalite on 2007-10-04
Update the BIOS or get an USB drive.

---

### Post by RedGreen on 2007-10-04
> **w4ett said:**
> If you have both optical drives on the same channel, please check that your jumper settings are correct....one needs to be set as master and the other set as slave.   Then go into your bios and run the drive detect to re-establish communication to the drives on the channel

I made sure and one of them is already set to master and the other to slave. Although I cant for the life of me seem to find a drive detect option in the BIOS, any idea where I might find that option.

Thanks for the help!

---

### Post by Pumalite on 2007-10-04
I encounter mine in 'IDE Configuration'

---

### Post by RedGreen on 2007-10-04
> **Pumalite said:**
> I encounter mine in 'IDE Configuration'

Hmm I am still not able to find it. I am searching for information about using Phoenix BIOS but not finding much luck.

---

### Post by w4ett on 2007-10-04
Under the Advanced Tab...IDE Configuration

[http://www.computerhope.com/help/phoenix.htm#01](http://www.computerhope.com/help/phoenix.htm#01)

---

### Post by Pumalite on 2007-10-04
Hope it helps:

[http://www.computerhope.com/help/phoenix.htm](http://www.computerhope.com/help/phoenix.htm)

[http://www.google.com/search?q=Phoenix+BIOS+Guide+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=Phoenix+BIOS+Guide+&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by RedGreen on 2007-10-04
> **w4ett said:**
> Under the Advanced Tab...IDE Configuration

[http://www.computerhope.com/help/phoenix.htm#01](http://www.computerhope.com/help/phoenix.htm#01)

My BIOS is a different version and does not have the same options.

Under Advanced:

[LIST]
[*]CPU Configuration
[*]PCIPnP
[*]Onboard Device Configuration
[*]SLI Configuration
[*]JumperFree Configuration
[*]LAN Cable Status
[*]PEG Link Mode
[*]Speech Configuration
[*]Instant Music
[/LIST]

---

### Post by w4ett on 2007-10-04
what motherboard are you using?

---

### Post by RedGreen on 2007-10-04
> **w4ett said:**
> what motherboard are you using?

ASUS A8N-SLI Deluxe

[http://www.asus.com/products.aspx?l1=3&l2=15&l3=148&model=375&modelmenu=1](http://www.asus.com/products.aspx?l1=3&l2=15&l3=148&model=375&modelmenu=1)

---

### Post by w4ett on 2007-10-04
> IDE Primary Master/Slave [Auto]; IDE Secondary Master/
Slave [Auto]
Select [Auto] to automatically detect an IDE hard disk drive. If automatic
detection is successful, the BIOS automatically fills in the correct values for
the remaining fields on this sub-menu. If the hard disk was already
formatted on a previous system, the setup BIOS may detect incorrect
parameters. Select [Manual] to manually enter the IDE hard disk drive
parameters. If no drive is installed select [None].
Configuration options: [None] [Auto] [Manual]


Looks like this is confgurable from the "Main" page of the bios for your board.

---

### Post by RedGreen on 2007-10-04
> **w4ett said:**
> Looks like this is confgurable from the "Main" page of the bios for your board.

Primary IDE Master
Primary IDE Slave
Secondary IDE Master
Secondary IDE Slave

Are already all set to auto.

---

### Post by w4ett on 2007-10-04
Well then, just a couple other things to check....Verify the IDE cable to the drives....verify your jumper setting...the jumper configuration can be totally different between manufacturers.....check each drive individually in the bios without the other present.   

If the bios isn't detecting it, the cables are secure and good, the jumpers are correct and power connections are good, then this might point to a hardware problem in one of the optical drives.

---

