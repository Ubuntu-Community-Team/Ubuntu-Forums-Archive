---
title: "Concatenate strings in shell script"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Wardazo on 2007-05-25
Hi

Trying to write my first shell script but for the life of me I can't work out how to concatenate a variable and a string... ie FILE="${DATE}.gz"

[PHP]#!/bin/sh
####mysql
DATE=`date +%Y-%m-%d`
mysqldump -u user -ppword --databases my_db> $DATE
gzip -f $DATE
####ftp
HOST='ftp.XXX.com'
USER='XXX'
PASSWD='XXX'
FILE="${DATE}.gz"   ###########Problem line##########
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
put $FILE
quit
END_SCRIPT
exit 0[/PHP]

Can someone enlighten me. I've tried everything... apart from the right way.

Ward

---

### Post by trak87 on 2007-05-25
I think you want

FILE=$DATE.gz

---

### Post by jyba on 2007-05-25
In this case FILE=$DATE.gz would work but in other cases it would fail. Wardazo is right to use FILE="${DATE}.gz" as an unambiguous way to combine a variable and a string. The braces ensure that the shell knows the name of the variable is DATE not DATE.gz

The mistake is elsewhere in the script, but as Wardazo doesn't tell us what error messages he got, it's difficult to guess where it goes wrong.

---

### Post by Wardazo on 2007-05-25
> **jyba said:**
> In this case FILE=$DATE.gz would work but in other cases it would fail. Wardazo is right to use FILE="${DATE}.gz" as an unambiguous way to combine a variable and a string. The braces ensure that the shell knows the name of the variable is DATE not DATE.gz

FILE-$DATE.gz works perfectly, but FILE="${DATE}.gz" doesn't.

However, according to what I've read FILE="${DATE}.gz" should work and be non-ambiguous.

Any clarificaton would be very welcome... I think I'm missing something.

Wardazo

---

### Post by jyba on 2007-05-25
The shell is better at diagnosing errors than you are. Could you please tell us what error messages you are getting.

Secondly, what shell sre you using?

**************

Edit: Okay, I've just looked back and seen that you're using /bin/sh, that is symlinked to dash! Try putting #!/bin/bash at the top of your script and see if it works.

---

### Post by Wardazo on 2007-05-26
Sorry,

My apologies, they BOTH work. I think I'd probably been awake too long:(. It's morning now and miraculously everything seems to work:p

Thanks for all the help

Ward

---

