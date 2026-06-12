---
title: "/home/share"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by brentoboy on 2006-06-12
is there a way to create a folder (like /home/share) that is read/write to all users, <b> and </b> make it so that if they save files in there, they continue to be read write to all other users?

if possible, is there also a way to make sure that files within never have execute permission (except sub-folders, which need execute permission in order to be opened -- I think)

I want to create a place for people to add music, pictures etc
It would be nice if only root could delete files in there.

Is any / all of this possible?

---

### Post by tonyr on 2006-06-12
Read [this]("http://www.psychocats.net/ubuntu/permissions.php").

---

### Post by brentoboy on 2006-06-12
ok,
how does that apply to what I am asking?

it is about sudo vs root.

when I said root above, I meant.... using sudo.

does anyone know how to create folder that has global read write, and that propegates that read-write permission to files saved inside it by other users?

that is the real question.

---

### Post by steve.horsley on 2006-06-12
You can create such a folder with:
[B]sudo mkdir /home/share
sudo chmod 777 /home/share[/B]
but you can't control the rights that the users apply to files created in there. The rights given to files is controlled by the users **umask**. This can be seen with the the command umask.

---

### Post by tonyr on 2006-06-12
Sorry about the wrong reference previously.  Look into **ACL (Access Control Lists)**.  The
package is **acl**.  It requires support in the kernel, but my configuration file
for 2.6.15-23 indicates that support is already there.  A lot of the articles about it out
there in google-land seem to be about using it with web servers, but it might apply
to your situation, too.

---

### Post by Oler1s on 2006-06-12
[quote=steve.horsley]You can create such a folder with:
[B]sudo mkdir /home/share
sudo chmod 777 /home/share[/B]
but you can't control the rights that the users apply to files created in there. The rights given to files is controlled by the users **umask**. This can be seen with the the command umask.[/quote]

"mkdir /home/share" creates a normal directory. For pedantic purposes, is sudo necessary on making the share directory?
"sudo chmod 777 /home/share" sets read, write, and execute permissions for all users. Again, is sudo required? Essentially, you create a root owner/group directory, which I think is a bad idea.

I would do:
mkdir /home/share
chmod 775 /home/share
create a non root owned directory with mkdir.
chmod 775 gives read, write, but not execute permissions to other users.

Also, umask is a solution, but is it not a bad idea? umask is a global setting.

---

### Post by brentoboy on 2006-06-12
to sudo or not to sudo?

--
doesnt matter which command line i use, because I created a user named "share" so /home/share exists.

sudo chmod seems necessary though (might as well have su-do it, because su has all power and can give all power, it wont get in the way for su to do it instead of share (share wont ever log in, and no other user has a write to mess with share's files anyway)
--

changing a user's umask seems insecure, because I want their files to belong to them, *unless* they put it in the share folder.  

could I get a second person to confirm that as admin I cant pre-enforce file permissions within a specific folder.  I have never heard of anyone doing this, but it seems like a reasonable request--as linux is all about having admin control security and enforcing things with rules rather than having to go through and hand do everything.  It seemd like it was probably possible.  Maybe it's not.

think outside the box.  If I mount a fat32 partition there, would it then be permission free?  I'm not sure how fat32 permissions are handled within linux, but I know there are complications.

---

### Post by bluenova on 2006-06-15
I would also like to do this.

I have a shared foler at the moment, which belongs to the group 'shared' which all users are member of. The problem is if a user moves a file into the shared folder, the file will still have the group of the user and not the shared group so nobody else can access it unless the user manually changes the group to shared for each file they move, which they don't always, so it needs to be automatic. When a user moves a file to the shared folder, the file will get the group 'shared'. I believe this is also what the original poster was requesting.

---

### Post by vruum on 2006-06-15
Not completely syure this is what you want, but the permissions tab in nautilus has a "set group id" tick box, which sets the group of all newly created files to the same as the folder itself.

---

### Post by bluenova on 2006-06-15
[QUOTE=vruum]Not completely syure this is what you want, but the permissions tab in nautilus has a "set group id" tick box, which sets the group of all newly created files to the same as the folder itself.[/QUOTE]
Yea, that's part of it, but what about for files that are moved to the shared folder, would it change the group?

---

### Post by vruum on 2006-06-15
nope, oops, copying them does change permissions, if that helps at all

---

### Post by bluenova on 2006-06-15
Ok great, I'll give it a go tonight when I get home. On a side note, what does sticky do in that list of options?

---

### Post by brentoboy on 2006-06-16
well, I found a good answer for this listening in on the dev forums.  It uses a python based daemon that watches a folder (or folders) and resets permissions for files that get placed inside.

I've got it working, and I will writeup a howto as soon as I finish.  then, I will link this forum to it.  If im lucky, I'll do it this weekend.

---

### Post by stengah on 2006-06-27
Brentoboy,

Any news on the tutorial with the python script/deamon? Sounds interesting!

---

### Post by brentoboy on 2006-07-06
here is the rough version of the howto

create a new folder
/home/share

download dirmonitor python script
[http://folk.uio.no/dagss/dirmonitor/](http://folk.uio.no/dagss/dirmonitor/)
follow the instructions for installing on that website

here is my /etc/dirmonitor.conf

```

<?xml version="1.0" encoding="utf-8"?>

<dir-monitor-config xmlns="http://www.fredtun.no/xmlns/dir-monitor-config/0.2">
	<!-- Each directory root is specified as a <dir/> element. Any subdirectories
	will also be monitored. -->
	<dir loc="/home/share">
		<!-- Use enforce elements to set owner, group, or permissions. Enforce
		elements can be overriden by enforce elements appearing later. -->
		<enforce owner="nobody" group="nogroup"/>
		<type-switch>
			<directory>
				<!-- Settings that take effect only for directories. -->
				<enforce permissions="rwxrwxrwx"/>
			</directory>
			<file>
				<!-- Settings that take effect for all files. -->
				<enforce group="nogroup"/>
			</file>
			<normal-file>
				<!-- Settings that take effect on non-executable files
				(in addition to those listed in <file/>). -->
				<enforce permissions="rw-rw-rw-"/>
			</normal-file>
			<executable-file>
				<!-- Settings that take effect on executable files
				(in addition to those listed in <file/>). -->
				<enforce permissions="rw-rw-rw-"/>
			</executable-file>
		</type-switch>
	</dir>
</dir-monitor-config>


```

---

