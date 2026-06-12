---
title: "Stuck with backports"
date: 2006-05-09
forum: Bug Reports / Support
---

### Post by Nikos_M on 2006-05-09
I have a problem with getting backports in my repositories.Actually this is in the file sources.list:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted multiverse universe
(without the # in front if you are curious :)  )
BUT when I start synaptic (or apt-get or aptitude) I dont get the Wesnoth package 1.1.2a.From what I checked actually I was not able to find anything from backports.Only the normal versions are there.

I have been circling around for 2 days with it so any help will be VERY APPRECIATED!

---

### Post by george_apan on 2006-05-09
Umm, did you do a

sudo apt-get update

first?

---

### Post by Nikos_M on 2006-05-09
[QUOTE=george_apan]Umm, did you do a

sudo apt-get update

first?[/QUOTE]

Yep plenty still no effect....

---

### Post by george_apan on 2006-05-10
Do you get any error messages while updating the database? Maybe the server was down. Could you try another mirror?

---

### Post by Nikos_M on 2006-05-12
i get this when i do apt-get update for example
BUT WESNOTH IS NOT THERE!At least not a version greater than  1.0.1...
And also twinkle that i am looking for is not there!

any thoughts?

---

### Post by Nikos_M on 2006-05-12
sorry i get this when i do apt-get update
-----------------------------------------------------------------

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-proposed Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Get:6 [http://rpm.rutgers.edu](http://rpm.rutgers.edu) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://rpm.rutgers.edu](http://rpm.rutgers.edu) breezy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-proposed/restricted Packages
Hit [http://rpm.rutgers.edu](http://rpm.rutgers.edu) breezy-backports/restricted Packages
Hit [http://rpm.rutgers.edu](http://rpm.rutgers.edu) breezy-backports/multiverse Packages
Hit [http://rpm.rutgers.edu](http://rpm.rutgers.edu) breezy-backports/universe Packages
Fetched 6B in 0s (10B/s)

---

### Post by george_apan on 2006-05-15
I'm afraid you'll have to wait a bit more to upgrade to dapper to get a newer version of wesnoth. See [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wesnoth&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=wesnoth&searchon=name&subword=1&version=all&release=all)
And twinkle is only available in dapper as well. [http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=twinkle&searchon=name&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=twinkle&searchon=name&subword=1&version=all&release=all)

So either wait until dapper stable comes out or upgrade to the latest flight.

---

