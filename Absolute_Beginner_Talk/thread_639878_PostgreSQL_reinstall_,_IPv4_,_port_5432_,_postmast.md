---
title: "PostgreSQL reinstall , IPv4 , port 5432 , postmaster issues"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Lars&#1758; on 2007-12-13
Hello Friends,

I am having experiencing extreme difficulty re-installing Postgresql 8.2.5 on my Xubuntu 7.10 distro. My eventual goal is to have Postgresql, PostGIS, and pgAdminIII working on my old box to be a GIS Server (Geographic Information Systems) ... but I'll get to the point.

At one point in time - when I first installed Postgresql 8.2.5 + PostGIS + pgAdminIII with Synaptic - I was able to connect to my PostgreSQL server through pgAdmin, create db's and everything.

Well, I re-installed Postgresql because I thought I needed to change some settings...yadda,yadda. And then the trouble hit!

What I'm experiencing is :

> LOG:  could not bind IPv4 socket: Address already in use
HINT:  Is another postmaster already running on port 5432? If not, wait a few seconds and retry.
WARNING:  could not create listen socket for "localhost"
FATAL:  could not create any TCP/IP sockets

...after trying to execute /usr/local/pgsql/bin/postgres -D /usr/local/pgsql/data

From what I understand, this is the step after ***initializing the database**> /usr/local/pgsql/bin/initdb -D /usr/local/pgsql/data * via [[COLOR="Blue"]http://www.postgresql.org/docs/8.2/interactive/install-short.html[/COLOR]]("http://www.postgresql.org/docs/8.2/interactive/install-short.html")

I have tried the advice given in the post [here]("http://ubuntuforums.org/showthread.php?t=413541&highlight=postgresql+reinstall") - but no worky either. I'm lost:confused:

A couple of other weird issues:
[LIST]
[*]I cannot find postmaster.pid to delete which was suggested at one point
[*]My /usr/local/pgsql/data seems to be missing some commands like ALTERUSER
[/LIST]

[SIZE="2"][COLOR="YellowGreen"]Please, please - I have no where else to go...I have scoured every Google search, every piece of PostgreSQL documentation, and more.[/COLOR][/SIZE][-o<[-o<

---

### Post by Lars&#1758; on 2007-12-19
bump!

plz let me know if i can clarify anything.

i know you're out there mr/mrs answer person.

---

### Post by keith3232 on 2008-05-28
Seems like you have PostgreSQL running already. Is there a PostgreSQL process running for the postgresql user?

---

