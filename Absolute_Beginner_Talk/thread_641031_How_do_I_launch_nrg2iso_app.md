---
title: "How do I launch nrg2iso app?"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by amazingDentist on 2007-12-14
I needed to convert an .nrg file to an ISO image file, so I installed the application "nrg2iso" through the terminal like this...

```
apt-get install nrg2iso
```

It installed completely.
However, I cannot for the life of me find where the application was installed to.
Where would it have been installed?  Or is there a terminal command code to assist in locating it?

---

### Post by amazingDentist on 2007-12-14
It is listed as an installed app in the synaptic Package Manager.
No way to launch it from there though... :confused:

---

### Post by taurus on 2007-12-14
Just type in the name of the program from a terminal.

```
nrg2iso **filename.nrg**
```

---

### Post by amazingDentist on 2007-12-14
When I type that command I receive this...

```
Nrg2Iso v0.4 by G. Kokanosky
released under the GNU GPL v2 or later

Usage :
nrg2iso image.nrg image.iso

--version    display version number
--help       display this notice

```

I don't think this did the conversion I wanted?

---

### Post by taurus on 2007-12-14
Here's your usage!

```
nrg2iso image.nrg image.iso
```
Again, assuming you are in the directory where image.nrg is and the name of the file is called **image.nrg**.

---

### Post by amazingDentist on 2007-12-14
hmmm, can't seem to get it to work.

heres what i typed...

```
nrg2iso /home/mike/Desktop/Windows XP Pro SP2 Full Student Release/Windows XP Pro SP2 Full Student Release/WINXPPROITT.nrg image.iso

```

and received this again...

```
Nrg2Iso v0.4 by G. Kokanosky
released under the GNU GPL v2 or later

Usage :
nrg2iso image.nrg image.iso

--version    display version number
--help       display this notice


```

Is that right?
Do i simply type the 2nd part as "image.iso"?
Where is the output directory supposed to be exactly?  In the same folder as the nrg file?


thank you for your time and patience.  noobs are difficult, i know. ;)

---

### Post by taurus on 2007-12-14
You need to understand a thing about filename.  There shouldn't be any space between words or special characters.  If you have space between words, then you need to put them in quotes.

```
nrg2iso "/home/mike/Desktop/Windows XP Pro SP2 Full Student Release/Windows XP Pro SP2 Full Student Release/WINXPPROITT.nrg"  WinXPPro.iso
ls -la
```

You now should see WinXPPro.iso from the output of the second command.

---

### Post by amazingDentist on 2007-12-14
Bingo.  It worked.
Thank you, taurus

---

### Post by nicholasemblow on 2008-03-10
Or u could use this script i made haha... or just dd it urself

```

#!/bin/bash

#************************************************#
#              isomaticEnergy.sh                 #
#           written by Nick Emblow               #
#                March 9, 2007                   #
#                                                #
#   Convert Nero NRG files to 9660 ISO files.    #
#************************************************#
inputFile=$1
outputFile=${inputFile%nrg}iso
E_NOTFOUND=75                       
E_FOUND=74   
E_WRONG_ARGS=65

script_parameters="image-file.nrg"

if [ $# -ne 1 ]
then
echo "#************************************************#"
echo "#              isomaticEnergy.sh                 #"
echo "#           written by Nick Emblow               #"
echo "#                March 9, 2007                   #"
echo "#                                                #"
echo "#   Convert Nero NRG files to 9660 ISO files.    #"
echo "#************************************************#"
  echo "Usage: `basename $0` $script_parameters"
  # `basename $0` is the script's filename.
  exit $E_WRONG_ARGS
fi

echo "Converting $inputFile to $outputFile"
                       
if [ ! -e "$inputFile" ]
then
  echo "$inputFile does not exists! Exiting."
  exit $E_NOTFOUND
fi 

if [ -e "$outputFile" ]
then
  echo "File $outputFile exists! Exiting."
  exit $E_FOUND
fi 

#dd is the "guts" of it. Because an NRG file is
#essentially an ISO file with an extra 307200 bytes appended
#to the beginning of the ISO information. 
dd if=$inputFile of=$outputFile bs=4096 skip=75



```

---

