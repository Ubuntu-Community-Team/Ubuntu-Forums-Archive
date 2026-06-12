---
title: "Installing Software Locally from backup"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by timnoc1456 on 2006-10-05
Hi,
	Only been a month in Linux & Ubuntu.This may seem unnecessary or trivial, but as a user on dialup it matters for me.

	Well when one installs or updates softwares or application in Ubuntu via, "Synaptic Package Manager/Add or Remove" it downloads the selected packages locally before installation" The place it downloads is at /var/cache/apt/archives.

	Now I am aware that one or other time my System would crash, most probably because of my own mistake and that I will have to make a fresh install. It would really be hard on me to re-download all the updates and packages of my previous installation through my slow dail-up from the various Repositories.

	Hence can anyone tell if its possible to backup the /var/cache/apt/archives folder and re-install from it all my previous update and packages to my or any fresh installation of Ubuntu

	I tried doing it using another hard disk on my PC and a fresh installation of Ubuntu, but the packages were not able to be installed via Synaptic Package Manager > Add downloaded packages. I even copied the whole backup of var/cache/apt/archives to the freshly installed Ubuntu's var/cache/apt/archives but it did not work.

	Thinking it might have something to do with the file /etc/apt/source.list and /etc/apt/source.save, I also tried copying it same from my old installation, but still no luck

---

### Post by daller on 2006-10-05
After copying the files back to the archive-folder, you should run "apt-get update" - Which fetches the latest files to be downloaded. Then run "apt-get dist-upgrade" - Which will only download the files which has changed in the period! (How long is there between?)

Alternately, you should look into "apt-proxy" if you have 2 computers, or more...

[https://help.ubuntu.com/community/AptProxy](https://help.ubuntu.com/community/AptProxy)

---

### Post by timnoc1456 on 2006-10-05
Thanks daller, I did as you told and was sucessful in re-installing my downloaded applications and updates; though I didn't understand . May be the repositories as well must be updated from net always to do it. Still I cannot figure out where the repositories settings files are ? And will copying those file as well will let me update from local folder without Internet?

Your links were also useful and informative though I still cannot figure out much of it.

Thanks Again:-D

---

