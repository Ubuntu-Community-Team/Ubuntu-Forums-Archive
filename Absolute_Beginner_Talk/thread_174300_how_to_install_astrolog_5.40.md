---
title: "how to install astrolog 5.40"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by jaara on 2006-05-11
I'm a beginner in linux. i've chosen ubuntu and i'm satisfied so far. what i need is astrolog 5.40 application and there's no package there, only source files. could someone help me with installation? thanks a lot.

---

### Post by frodon on 2006-05-15
If you want to learn how install things with ubuntu you can start with my small guide : 
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)

---

### Post by steve.horsley on 2006-05-15
You are in trouble with that one. I notice it is 8 years old. Anyway, they don't have a Linux source. I downloaded the "unix" source:
[http://www.astrolog.org/ftp/ast54unx.shr](http://www.astrolog.org/ftp/ast54unx.shr)
and put it in its own directory. 
I installed the C compiler by using synaptic to install the package **build-essential**
With a command prompt I changed to the astrolog directory (where I downloaded it to) 
**cd astrolog** and then executed the file with the command
**. ast54unx.shr**
This created a bunch of other files in that directory - all the source files. Then I entered the command:
**make**
And this is where the plot goes wrong - compile errors. I have no idea how to fix these. I guess the source isn't compatible with gcc.

---

### Post by Perfect Storm on 2006-05-15
It's in the multiverse (well, at least in Ubuntu Dapper). So if you have enable multiverse in your sourcelist, then:

```
sudo apt-get install astrolog
```

---

### Post by catlett on 2006-05-15
[QUOTE=frodon]If you want to learn how install things with ubuntu you can start with my small guide : 
[http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118)[/QUOTE]
Very nice guide! I wish it was easier to find. I've never seen it before this post. It is exactly how I like information. Straight forward, logical and with real examples that I can copy even if I don't understand. If you don't mind I'd like to refer people to your thread [http://ubuntuforums.org/showthread.php?t=153118](http://ubuntuforums.org/showthread.php?t=153118) along with monkeyblog [http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html) (sorry to cut into the thread I'll be going now)

---

### Post by steve.horsley on 2006-05-17
[QUOTE=Artificial Intelligence]It's in the multiverse (well, at least in Ubuntu Dapper). So if you have enable multiverse in your sourcelist, then:

```
sudo apt-get install astrolog
```[/QUOTE]

AArgh!
Searching synaptic was the first thing I did - it should be the first place anyone ever looks for software. Either it wasn't there then, or I cat'n tpye.

---

### Post by merlinus on 2007-04-23
> **Artificial Intelligence said:**
> It's in the multiverse (well, at least in Ubuntu Dapper). So if you have enable multiverse in your sourcelist, then:

```
sudo apt-get install astrolog
```

I did this, and got a message that it is installed.

There is an icon in /usr/games, but when I click on it, nothing happens.

Thanks for any assistance.

-merlin

---

### Post by Perfect Storm on 2007-04-23
Type
```
astrolog
```
in the terminal.

---

### Post by merlinus on 2007-04-23
> **Artificial Intelligence said:**
> Type
```
astrolog
```
in the terminal.

This gives me text input options, and outputs the same.  From what I read at the website, it is *supposed* to create graphical charts, no?

Thanks....

-merlin

---

### Post by Terl on 2007-04-23
> **merlinus said:**
> This gives me text input options, and outputs the same.  From what I read at the website, it is *supposed* to create graphical charts, no?

Thanks....

-merlin

It looks like it is supposed to do charts.  Did you read [The Doucumentation]("http://www.astrolog.org/ftp/Helpfile.540") on the site?

---

### Post by Oceola on 2007-05-11
Astrolog doesn't show up in any of the US repositories. For some reason it's not in the multiverse. There is a debian package 5.40-3 and a 5.40-2. 
Gdebi recognizes it in Dapper when downloading in Firefox and I may try Gdebi or move the package to "/var/cache/apt/archives" then "CD /var/cache/apt/archives" and do the "sudo dpkg -i <package name>". I wound up shifting a lot of files from my old box to this one by downloading only and then copying the files to the apt archives and using dpkg with proper results. Haven't done this yet. One thing I was wondering, there's a file "astrolog.cgi.gz" and I'm wondering if you need to install the Ubuntu CGI support in order to resolve the display issues, might be worth a shot.

Good Luck

Update:
Gdebi had a dependency issue with the 5.40-3 as did the dpkg -i install method BUT the dependency appears to be in what Astrolog is looking for in the way of libc6. The version from Debian archives does not have the Ubuntu modification or name designation.
Gdebi just stopped dead but the dpkg -i noted the libc6 version error and did not configure but when opening a terminal and typing in Astrolog without commands, the location, name and time sequence started properly as I have seen it in the past. I input information for a simple "here and now" list and retrieved a text output. I checked the output against the Swiss Ephemeris and also the same time in Kstars. As usual the tropical is off a sign for the closer planets due to precession but are where they are supposed to be for Saturn, etc.. It showed Jupiter in Retrograde in Sagitarius which is in agreement since April.

No help file showed up in Yelp but I ciopied the Help.gz file to simple text file and put it where I could get to it easy enough. There are a number of commands in the help file and I am thinking the command input at startup will have much to do with how information is displayed graphically. There is no Icon under games.

---

### Post by Oceola on 2007-05-16
The following occurs if having installed Astrolog 5.40-3 using the plain Debian package. 
Synaptic shows it as a broken package even though it functions in the terminal and will remove it if updating other pacakges. Might be nice if one had the option to leave it alone or someone would modify the Debian Astrolog 5.40-3 package to recognice the Ubuntu version of Libc6 and place it in the US Main. Backport or Multiverse repositories. 

I did some further exploration of the "broken" install and using the terminal and inputting "astrolog -v -a -j" retrieved the following info. Package seems to agree within a couple minutes of Glunar Clock, Kstars and some of my feeble manual math skills.
Also there are switch values for the various house system (14) with one no house system and switches for Vedic, sidreal or tropical calculations. 

Note: Kstar seems to have a two day Lunar issue with the true Spring Equinox but agrees on the Solstices.

All the switches seem to function but the graphic display so far has returned older form Dos like text graphics instead of colored lines and pretty wheels but the info seems relative and accurate. 
Also seems to accept Minutes, degrees and seconds for Longitude and Latitude instead of the simplified decimal input which seems to allow for more accuracy.

Today at 7:02 EST 76W x 39N near Annapolis
Note: it prints in the proper format it just copies out of place like this.
Body  Locat. Ret. Lati. Rul.      House  Rul. Veloc.    Placidus Houses.
Sun : 25Tau13   - 0:00' (-) [12th house] [-] +0.964  -  House cusp  1: 13Gem44
Moon: 20Tau16   + 4:38' (e) [12th house] [-] ______  -  House cusp  2:  5Can53
Merc: 10Gem09   + 1:53' (R) [12th house] [F] +1.898  -  House cusp  3: 26Can44
Venu:  8Can56   + 2:41' (-) [ 2nd house] [R] +1.083  -  House cusp  4: 20Leo22
Mars:  0Ari40   - 1:30' (R) [11th house] [-] +0.758  -  House cusp  5: 21Vir05
Jupi: 17Sag26 R + 0:44' (R) [ 7th house] [-] -0.109  -  House cusp  6:  1Sco33
Satu: 18Leo44   + 1:17' (F) [ 3rd house] [-] +0.046  -  House cusp  7: 13Sag44
Uran: 18Pis07   - 0:45' (-) [10th house] [-] +0.030  -  House cusp  8:  5Cap53
Nept: 22Aqu01   - 0:15' (-) [10th house] [-] +0.005  -  House cusp  9: 26Cap44
Plut: 28Sag28 R + 7:03' (-) [ 7th house] [-] -0.021  -  House cusp 10: 20Aqu22
Chir: 16Aqu01   + 6:51' (-) [ 9th house] [-] +0.005  -  House cusp 11: 21Pis05
Cere: 22Ari56   - 7:49' (-) [11th house] [-] +0.374  -  House cusp 12:  1Tau33
Pall: 14Pis36   +16:25' (F) [10th house] [e] +0.210
Juno: 14Lib04 R +10:04' (R) [ 5th house] [e] -0.111     Car Fix Mut TOT   +:11
Vest: 20Sag20 R + 7:35' (-) [ 7th house] [-] -0.163  Fir  2   1   3   6   -: 9
Node: 12Pis30 R + 0:00' (d) [10th house] [-] ______  Ear  0   3   1   4   M:15
S.No: 12Vir30 R + 0:00' (d) [ 4th house] [-] ______  Air  1   2   2   5   N: 5
Fort:  8Gem47   _______ (d) [12th house] [R] ______  Wat  1   1   3   5   A:13
Vert:  7Sco18   _______ (-) [ 6th house] [d] ______  TOT  4   7   9  20   D: 7
East: 25Tau07   _______ (-) [12th house] [-] ______                       <:10

Press return to continue scrolling >

  1:     Sun (Tau) Con (Tau) East Point - orb: +0:06' - power: 16.92
  2:     Sun (Tau) Con (Tau) Moon       - orb: +4:56' - power: 12.43
  3:    Moon (Tau) Squ (Leo) Saturn     - orb: -1:32' - power: 11.32
  4:    Moon (Tau) Squ (Aqu) Neptune    - orb: -1:44' - power: 10.97
  5:     Sun (Tau) Squ (Aqu) Neptune    - orb: +3:12' - power:  9.60
  6:    Moon (Tau) Sex (Pis) Uranus     - orb: +2:09' - power:  7.28
  7: Jupiter [Sag] Squ (Pis) Uranus     - orb: +0:41' - power:  7.22
  8: Mercury (Gem) Con (Gem) Fortune    - orb: +1:21' - power:  6.05
  9:    Moon (Tau) Squ (Aqu) Chiron     - orb: +4:15' - power:  5.62
 10:    Mars (Ari) Squ [Sag] Pluto      - orb: +2:12' - power:  5.49
 11: Jupiter [Sag] Tri (Leo) Saturn     - orb: -1:18' - power:  4.88
 12: Jupiter [Sag] Con [Sag] Vesta      - orb: +2:54' - power:  4.39
 13:  Saturn (Leo) Opp (Aqu) Neptune    - orb: -3:17' - power:  4.25
 14:  Uranus (Pis) Squ [Sag] Vesta      - orb: -2:13' - power:  4.10
 15:    Node [Pis] Opp [Vir] S.Node     - orb: +0:00' - power:  4.00
 16: Neptune (Aqu) Sex (Ari) Ceres      - orb: +0:55' - power:  3.81
 17:  Uranus (Pis) Con (Pis) Pallas     - orb: +3:31' - power:  3.73
 18:  Saturn (Leo) Opp (Aqu) Chiron     - orb: -2:42' - power:  3.69
 19: Jupiter [Sag] Squ (Pis) Pallas     - orb: -2:49' - power:  3.58
 20:  Saturn (Leo) Tri [Sag] Vesta      - orb: +1:36' - power:  3.47
 21: Jupiter [Sag] Sex (Aqu) Chiron     - orb: -1:24' - power:  3.45
 22:   Venus (Can) Tri (Sco) Vertex     - orb: -1:38' - power:  3.45
 23: Neptune (Aqu) Sex [Sag] Vesta      - orb: +1:40' - power:  3.25
Press return to continue scrolling >
 24:     Sun (Tau) Squ (Leo) Saturn     - orb: -6:29' - power:  3.03
 25:     Sun (Tau) Sex (Ari) Mars       - orb: -5:27' - power:  2.66
 26: Mercury (Gem) Squ (Pis) Pallas     - orb: -4:26' - power:  2.20
 27:  Chiron (Aqu) Tri [Lib] Juno       - orb: +1:56' - power:  2.17
 28: Jupiter [Sag] Sex [Lib] Juno       - orb: +3:21' - power:  1.99
 29: Mercury (Gem) Tri [Lib] Juno       - orb: +3:55' - power:  1.98
 30:   Ceres (Ari) Tri [Sag] Vesta      - orb: +2:35' - power:  1.89
 31:  Saturn (Leo) Tri (Ari) Ceres      - orb: -4:12' - power:  1.80
 32:    Moon (Tau) Sex (Pis) Pallas     - orb: +5:40' - power:  1.71
 33:   Venus (Can) Squ [Lib] Juno       - orb: +5:08' - power:  1.60
 34: Jupiter [Sag] Sex (Aqu) Neptune    - orb: +4:35' - power:  1.42
 35: Neptune (Aqu) Con (Aqu) Chiron     - orb: +5:59' - power:  1.09
 36:  Saturn (Leo) Sex [Lib] Juno       - orb: -4:39' - power:  1.01
 37: Jupiter [Sag] Tri (Ari) Ceres      - orb: +5:30' - power:  0.96
 38:   Pluto [Sag] Tri (Ari) Ceres      - orb: -5:31' - power:  0.95
 39:   Venus (Can) Tri (Pis) Pallas     - orb: -5:39' - power:  0.87
 40:  Chiron (Aqu) Sex [Sag] Vesta      - orb: -4:19' - power:  0.84
 41:    Juno [Lib] Tri (Gem) Fortune    - orb: +5:17' - power:  0.73
 42: Mercury (Gem) Tri (Aqu) Chiron     - orb: -5:52' - power:  0.73
 43:  Pallas (Pis) Squ [Sag] Vesta      - orb: -5:44' - power:  0.72
 44:  Pallas (Pis) Squ (Gem) Fortune    - orb: -5:48' - power:  0.69


  Planet:    Position      Aspects    Total Rank  Percent
Press return to continue scrolling >
     Sun:   47.5 ( 6) +  18.9 ( 8 ) =   66.4 ( 6) /   7.7%
    Moon:   42.5 ( 7) +  32.9 ( 3) =   75.4 ( 3) /   8.7%
 Mercury:   57.5 ( 3) +   3.3 (16) =   60.8 ( 8) /   7.0%
   Venus:   67.5 ( 1) +   1.6 (17) =   69.1 ( 5) /   8.0%
    Mars:   32.5 ( 8 ) +   9.5 (12) =   42.0 (10) /   4.9%
 Jupiter:   50.0 ( 5) +  23.1 ( 6) =   73.1 ( 4) /   8.5%
  Saturn:   25.0 (10) +  36.5 ( 2) =   61.5 ( 7) /   7.1%
  Uranus:   55.0 ( 4) +  22.8 ( 7) =   77.8 ( 2) /   9.0%
 Neptune:   67.5 ( 2) +  41.2 ( 1) =  108.7 ( 1) /  12.6%
   Pluto:   15.0 (13) +   6.1 (13) =   21.1 (15) /   2.4%
  Chiron:    5.0 (16) +  24.3 ( 4) =   29.3 (13) /   3.4%
   Ceres:    5.0 (17) +  11.9 (10) =   16.9 (17) /   2.0%
  Pallas:   25.0 (11) +  17.4 ( 9) =   42.4 ( 9) /   4.9%
    Juno:   30.0 ( 9) +  10.9 (11) =   40.9 (11) /   4.7%
   Vesta:   10.0 (15) +  23.7 ( 5) =   33.7 (12) /   3.9%
    Node:   20.0 (12) +   4.0 (14) =   24.0 (14) /   2.8%
  S.Node:   15.0 (14) +   4.0 (15) =   19.0 (16) /   2.2%
   Total:  570.0      + 292.3      =  862.3      / 100.0%

---

### Post by dwblas on 2007-12-11
> You are in trouble with that one. I notice it is 8 years old. Anyway, they don't have a Linux source. I downloaded the "unix" source: [http://www.astrolog.org/ftp/ast54unx.shr](http://www.astrolog.org/ftp/ast54unx.shr) and put it in its own directory.
I installed the C compiler by using synaptic to install the package build-essential
With a command prompt I changed to the astrolog directory (where I downloaded it to)
cd astrolog and then executed the file with the command
. ast54unx.shr
This created a bunch of other files in that directory - all the source files. Then I entered the command:
make
And this is where the plot goes wrong - compile errors. I have no idea how to fix these. I guess the source isn't compatible with gcc.I just compiled source because I'm on a 64 bit system.  I removed the X11 libs dependency and everything went fine.  Specifically, I commented line 55 in astrolog.h
//#define X11 /* Comment out this #define if you don't have X windows, or */    
            /* else have them and don't wish to compile in X graphics.  */

 as well as lines 442-448
//#ifdef MOUSE                                                                  
//#ifdef GRAPH                                                                  
//#ifndef ISG                                                                   
//"If 'MOUSE' is defined 'X11', 'WIN', 'MSG', 'BGI', or 'MACG' must be too"     
//#endif                                                                        
//#endif /* GRAPH */                                                            
//#endif /* MOUSE */ 
make worked fine then and since I don't use the X11 libs to display, it doesn't make any difference.  I would guess that installing xlibs-dev would also work.  If anyone has tried it, please post the results.

---

