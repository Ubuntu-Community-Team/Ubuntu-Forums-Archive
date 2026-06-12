---
title: "Stuck already md5 absolute beginner"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by swanns on 2006-12-09
I'm having trouble getting the md5 hashes to match.

I have checked the version I've downloaded and it's hash at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and it is identical.

The problem is I can't get it recognised - I go into properties then file hashes and click compare and then it asks where I want to look for code? Well, where do I? Have tried inputting url and this doesn't work - I am doing something wrong at this point 'cos like i say they do match I just can't make them think they do. Go on, point out obvious answer - I know I am being thick.

Thanks.

---

### Post by taurus on 2006-12-09
Well, here's a good guide for you.

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by PapaNerd on 2006-12-09
Being somewhat lazy and not especially fond of manually comparing the md5 hashes on .iso files, I downloaded the hashes into a text file which I named "md5sums" and then created a script which I called "confirm" and run from a terminal window.  

Here is the script:

#!/bin/bash
# Confirm the checksums of files in this directory.
if [ -z "$1" ]
  then LIST=`ls *iso`
  else LIST=$*
  fi
CONFIRM_LOG="confirmation-log"
for FILE in `echo $LIST`
  do
    GOOD_SUM=`grep "	$FILE" md5sums | awk '{print $1}'`
    if [ "$GOOD_SUM" == "" ]
      then GOOD_SUM="<none>"
      fi
    FILE_SUM=`md5sum $FILE | awk '{print $1}'`
    NOW=`date '+%Y%m%d-%H:%M'`
    if [ "$FILE_SUM" == "$GOOD_SUM" ]
      then echo "$NOW - Checksum Confirmed!	File:  $FILE"
      else
	echo "$NOW - Checksum MISMATCH!	File:  $FILE"
	echo "    Expected:  $GOOD_SUM"
	echo "    Found:     $FILE_SUM"
      fi
  done | tee -a $CONFIRM_LOG
exit

Be sure to enable executable permissions on the script (chmod 755 confirm).  Then, you can either run it on a single file:
  ./confirm ubuntu-6.10-alternate-i386.iso
or on all the .iso files in the directory:
  ./confirm
The script also keeps a log of what you've already confirmed.

Hope this helps!

---

