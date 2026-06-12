---
title: "Installation: Cinelerra, SMC (?)"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Chake99 on 2007-01-21
On kubuntu dapper drake here, and I'm trying to install

[http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

[http://www.secretmaryo.org/index.php?page=game_downloads&sid=sid=68121dbfc65c592a336c4b76c1d3a884](http://www.secretmaryo.org/index.php?page=game_downloads&sid=sid=68121dbfc65c592a336c4b76c1d3a884)

For Cinelerra I dled all of the .debs under the ubuntu flag to my home directory and tried to get them to install with kubuntu package manager, but it yelled at me about dependencies.

For SMC I dled the RPM alien'd it to a .deb, but once installed it failed to work.  

How would I get these programs to work? Download and compile from source? What files in that case?

Help would be very greatly appreciated.

---

### Post by Marsolin on 2007-01-21
Try adding this line to your sources.list file.

deb [http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/](http://www.kiberpipa.org/~minmax/cinelerra/builds/sid/) ./

Also make sure that the Ubuntu universe and multiverse repositories are enabled.

I haven't tried it myself, but doing those two things are what I would start with.

---

