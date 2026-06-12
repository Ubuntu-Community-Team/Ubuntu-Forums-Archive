---
title: "need a walk-through...calendar"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by sailor2001 on 2006-09-05
/home/sailor/Desktop/calendar-2.71.tar.gz
mounted on the desktop, also untared and sitting on the desktop..no deb or rpm extentions here.,, Have build-essentials and checkinstall and repositories all updated....now, how to install? Have been trying without luck on the tutorials

---

### Post by croak77 on 2006-09-05
What is the program? Where did you get it? Is there an INSTALL or README file in the tar.gz?

---

### Post by sailor2001 on 2006-09-05
fuzzymonkey......no install file
    1. Install scripts

    ftp mycalendar-xxx.tar.gz to your cgi-bin/ directory on your server
    $ tar -zxvpf mycalendar-xxx.tar.gz
    this will create a calendar/ directory in that directory

    2. edit template.html to match your site

    To customize the look, simply edit template.html.  This file can be created with any html editor or text editor as long as it retains the hidden HTML comment,  <!-- content --> .  This comment is where the content (calendar) will be placed.

    3.  password protect protected/ directory

    Use htaccess or some other method to password protect the protected/ dirctory.  Doing this will require your users to supply a password if they ever attempt to edit any events.

    4.  Move calendar.css to an html servable location, and specify it in sitevariables.pl.


HOW TO USE

    Just point your browser at it

    e.g.- [http://www.yoursite.com/cgi-bin/calendar/index.cgi](http://www.yoursite.com/cgi-bin/calendar/index.cgi)

    If you get an internal server error, check your web server error logs or run it from command line so that you can see what is going wrong.  See my docs/FAQ.html on my script page for more info.

---

### Post by croak77 on 2006-09-05
Do you have apache or a webserver installed?

---

### Post by sailor2001 on 2006-09-05
no      maybe this is something I don't need.........thought I'd give it a try

---

### Post by croak77 on 2006-09-05
Yeah...it's a web calendar meant for you to host on your web server.If you are looking for a online calendar software, try Google Calendar. Or for desktop app, try mozilla sunbird. Evolution has a calender too. There is also webcalendar, which is in the repo, but it requires php and a db like mysql.

---

### Post by sailor2001 on 2006-09-05
ok. thanks croak for the info....I was really hoping for a program that would design calendars.........

---

