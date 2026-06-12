---
title: "[SOLVED] IP Address tracker"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Meph1st0 on 2008-01-26
In Winblows I used to have a utility that would watch my public IP address and send me an email with my new IP address if it had changed.  I need the same sort of utility for Ubuntu.  Can anyone point me in the right direction?

---

### Post by zazuge on 2008-01-26
something like this ?
w3m [http://www.checkip.net](http://www.checkip.net) -dump | grep "Current IP Address" | sed 's/^.*: //g' | read MYIP_NOW && if [ "$MYIP_NOW" != "$MYIP" ]; then mail -s "IP Change" < `w3m [http://www.checkip.net](http://www.checkip.net) -dump -T text/html ` you@locahost ; fi

---

### Post by Meph1st0 on 2008-01-26
Ok, umm....,....huh?

I'm a huge Linux nube.  There wouldn't happen to be some sort of a gui utility out there?

---

### Post by Whiffle on 2008-01-26
Why not setup dynamic dns?  [http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html](http://ubuntulinuxhowto.blogspot.com/2006/06/dynamic-dns-no-ip.html)

---

### Post by Spitphire on 2008-01-26
here's something you could use as well, requires the sendEmail package..

make a script containing the following, of course modify the personal info:

```

#!/bin/sh

FILE=/where/to/locate/temp/file

NEWIP=`wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'`[ -e $FILE ] && OLDIP=`cat $FILE`

if [ "$NEWIP" != "$OLDIP" ]; then
echo "New IP: $NEWIP" | sendEmail -f FROMWHO@DOMAIN.COM -t TOWHO@DOMAIN.COM -u "IP ADDRESS Changed" -m "$NEWIP" -s smtp.gmail.com -o tls=yes -xu USERNAME -xp PASSWORD
echo $NEWIP > $FILE
echo "Notified by email ($EMAIL)"
fi

```

```
chmod +x yournewfile.sh
```

if you need to run it every 30 minutes or so, add to crontab.  it will only e-mail you if the ip address changes..

---

### Post by Meph1st0 on 2008-01-26
Sweet! I'm going to give that script a try first.  


As far as the Dynamic DNS goes, I've heard of it and want to try it out but know nothing about it.  I"m sure it'll fix my problem.  I've got a domain name registered all I gotta do is set it up right?

---

### Post by Meph1st0 on 2008-01-26
Wait, I just read the How To that Whiffle supplied and that looks easy as cake so I'm going to try THAT one first.  Thanks again SpitPhire. :)  You'll be my backup.

---

