---
title: "Data &amp; Program Directories"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by drfox on 2006-04-29
Where should I keep my data? Does it belong in /home/user_name/data or something like that? What if more than 1 person accesses the computer and we have data shared? Then, where should it be kept?

If I want to install a program that I have saved to my desktop, to what directory do I install?  I seem to be having problems because so many directories belong to root.

Thanks.

Larry

---

### Post by jazzmuzik on 2006-04-29
Keep data in your user directory. There are no rules for this, but just as a suggestion, you might use /home/user/data . You can branch off of that:

/home/user/data/music
/home/user/data/taxes
/home/user/data/images
/home/user/data/movies
/home/user/data/documents

Shared data could be anywhere you want. You just need to modify the directory ownership and permissions to allow others to access it. Be careful doing that. And you can control who gets access by creating a group name and then adding user names to that group. Only users in that group will be able to access the directory you've set up with that group's name.

A good place for shared data might be a directory in /home, like /home/shared especially if you created a separate partition for /home during the installation process. Then if you ever do a new install you can format everything except the /home partition and your data is safe. (Note however that many files worth saving are scattered about the system. Perhaps this is unfortunate. One example is database files. MySQL database files are stored under /var. Another example might be the Apache web server html files if you've created a local website.)

For installing programs, first choice should be to install Ubuntu .deb files from the repositories via the command line or Synaptic (or other package manager). So if there's a program you want to install, see if it is already available in Synaptic before downloading something from a website. Second choice would be to install a deb file from a non Ubuntu source. Third choice would be to install a Debian deb file from the Debian repositories. Fourth would be a non deb file, like a tar.gz. I'm leary of doing this because I don't want to mix debs and non-debs. Another good option is to install in your user directory. For example, I downloaded [Firefox 1.5.0.2](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.2/linux-i686/en-US) and installed it in my user directory. That way I don't have to wait for Ubuntu to create an upgraded deb package. I had to install a couple of libraries to make that work, but they were available via Synaptic.

---

