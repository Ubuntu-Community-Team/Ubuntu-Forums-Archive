---
title: "Mozilla Calendar .ics Location?"
date: 2005-09-29
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2005-09-29
I am trying to figure out where mozilla calendar saves the .ics files so i can just copy and paste it.  Can anyone tell me or tell me how to trace it down?

I don't even know if i should be posting this in here?  Where should i be posting this?

---

### Post by davmac on 2005-09-29
On the "Places" menu there is a "Find files..." option. Is this what you mean?
You could also open up a terminal and type "sudo find / -name 'the_pattern_you're_looking_for' -print".

There's a good introduction to using the find command at [http://www.linux.ie/newusers/beginners-linux-guide/find.php](http://www.linux.ie/newusers/beginners-linux-guide/find.php)

HTH,

Dave Mac

---

### Post by hansoffate on 2005-09-29
k well i found it.  Is there anyway i can make a macro or something that will do this for me

cp /home/hans/.mozilla/default/z9viishq.slt/Calendar/CalendarDataFile.ics /var/www/phpicalendar-2.0.1/calendars/

then rename /var/www/CalendarDataFile.ics  to hanscalendar

and replace the old one?

---

### Post by davmac on 2005-10-01
You need a script!

In a terminal type "gedit myscript"

Then insert into the file "#! /bin/bash" without the quotes, on the first line.

Then just put the rest of your commands below this.

Save the file and then, to make it executable type "chmod a+x myscript"

To run the script you'll need to type ./myscript

Hope this helps,

Dave Mac

---

