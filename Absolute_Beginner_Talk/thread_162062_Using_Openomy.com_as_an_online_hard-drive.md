---
title: "Using Openomy.com as an online hard-drive"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-04-18
Hello,
I think I've found an answer to a free online hard-drive. No longer do I have to wait for google to come out with their G-drive. And gmail users don't have to try making their email account a hard drive. The maker of openomy.com has invited anybody to [use openomy as their free online harddrive]("http://www.iseff.com/2006/03/google-drive-gdrive-already-exists-its.html") . It's free to use. The only catch is that their's a 1 GB limit for the account.


But how do we get openomy to do bulk uploads and downloads? It seems you need to be a programmer to devise the methods.

Can anyone help? 

Thanks.

UPDATE: I fixed the link

---

### Post by unbuntu on 2006-04-18
[QUOTE=hanzj]Hello,
I think I've found an answer to a free online hard-drive. No longer do I have to wait for google to come out with their G-drive. And gmail users don't have to try making their email account a hard drive. The maker of openomy.com has invited anybody to [use openomy as their free online harddrive]("http://www.iseff.com/2006/03/google-drive-gdrive-already-exists-its.htm") . It's free to use. The only catch is that their's a 1 GB limit for the account.


But how do we get openomy to do bulk uploads and downloads? It seems you need to be a programmer to device the methods.

Can anyone help? 

Thanks.[/QUOTE]

Wow, thanks for the cool site.  ([www.openomy.com](www.openomy.com), not the link, which is dead by the way:( )

As to your question, I haven't looked up the API yet, but for bulk upload you can play around with their upload interface and not touching the API at all.

Off the top of my head, one way to do it may be like this:  you can get the DOM information for that page using Firefox's DOM inspector, get the field name used for filename to upload and the action behind the upload button, and write a Python script to do the upload without going to their interface, and making batch upload can be easily extended from that point.

However, in a long run, using their published API would be a better choice.  Again, thanks for the info.

---

### Post by unbuntu on 2006-04-18
The following code is taken from their API wiki, the perl script that uploads a single file:
```

#! /usr/bin/perl

use strict;
use warnings;

use LWP;
use HTTP::Request::Common;
use Digest::MD5 qw(md5_hex);

my $b = LWP::UserAgent->new;
my $url = "http://www.openomy.com/api/rest/";

my $filename = "/home/iseff/testUpload.txt";
my $applicationKey = "1234567890abcd1234";
my $confirmedToken = "abcdefghijklmnop1234567890";
my $privateKey = "0123456789";
my $method = "Files.AddFile";
my $tagID = "1";
my $unhashed = "applicationKey=$applicationKey"."confirmedToken=$confirmedToken";
$unhashed .= "method=$method"."tagID=$tagID"."$privateKey";
my $signature = hash($unhashed);

my $response = $b->request(POST "$url",
                           Content_Type => 'form-data',
                           Content => [ method => "$method",
                                        applicationKey => "$applicationKey",
                                        confirmedToken => "$confirmedToken",
                                        signature => "$signature",
                                        tagID => "$tagID",
                                        fileField => ["$filename"],
                                        ]
                           );

print $response->content . "\n";


sub hash
{
    my ($query) = @_;
    return uc(md5_hex($query));
}

```

Then set up a list of files, and iterate the list, call this procedure repeatedly, and there you go.

---

### Post by hanzj on 2006-04-18
Unbuntu,
You are most welcome. 
I fixed the link.
Are you planning on using openomy as an online drive? If so, let me know if you get it working. 
I'll try your script when I get back to my linux computer.

---

### Post by unbuntu on 2006-04-18
[QUOTE=hanzj]Unbuntu,
You are most welcome. 
I fixed the link.
Are you planning on using openomy as an online drive? If so, let me know if you get it working. 
I'll try your script when I get back to my linux computer.[/QUOTE]

Yes, I think I will.  Last year I registered a project at sourceforge in which I intended to use gmail as a "FTP-like" storage.  However it got stuck due to my schedule and lack of planning.  The problem with gmail is that although at that time gmailfs is published which aimed to use gmail storage as part of your file system, google doesn't endorse the idea.

This openomy.com releases their API and encourages people to make applications on this API.  It's a good sign.  However, my worry for this kind of online service is how long will they last before they begin to charge you for some decent service.  Like rapidshare.de (or something like that), free access requires you to wait for one and a half hour between two downloads, which is ridiculous.  Well, let's see how long this thing will last.:-D

---

### Post by hanzj on 2006-04-18
I think i read in their faq that they will try to keep it running as long as possible. don't know their business model yet.

---

### Post by iseff on 2006-06-20
Hey guys,
Along with a partner, I actually developed and run Openomy. (As an aside, we're both also Ubuntu users, which is how I found this post.)

I can fill in some details about the project, and also give some insight into how we're planning on moving forward.

First, some questions answered: 
I haven't attempted to look at the Perl script written here, though it looks a lot like what I wrote on our documentation, so I would assume it'd do the job of bulk uploading. :)

However, for us linux users, we have some nicer interfaces. My partner, Maurice, wrote a FUSE wrapper (in Ruby) which we call OpenomyFS (OFS, for short) which you can learn about and download (and is open source) here:
[http://mauricecodik.com/projects/ofs/](http://mauricecodik.com/projects/ofs/)

Essentially, it mounts your Openomy account as a directory (so you can use all your files as you would a local hard disk).

We have a pretty active and growing dev community, a couple of whom have created notable projects for this type of stuff. First, someone created a Python version of the FUSE mount:
[http://documentation.openomy.com/index.php/Openomy_fs.py](http://documentation.openomy.com/index.php/Openomy_fs.py)

Second, the same person also created another very useful python script, Openomy_sync.py, which syncs directories with your Openomy account:
[http://documentation.openomy.com/index.php/Openomy_sync.py](http://documentation.openomy.com/index.php/Openomy_sync.py)

Third, another user created a multi-platform application (written in Java) which is a WebDAV gateway to our APIs. This allows you to do many things, including mount the gateway as a drive (in all operating systems: Linux, Mac, and Windows). It's not fully complete (read-only, no writing), but it's a great start!
[http://jopendav.phowar.net/i2.html](http://jopendav.phowar.net/i2.html)

There's also a QT Openomy client for browsing and uploading, written in C++, but I haven't actually seen anything but screenshots yet (however, it looks awesome and polished!):
[http://groups.google.com/group/Openomy-Developers/browse_thread/thread/8de4665fa388064d](http://groups.google.com/group/Openomy-Developers/browse_thread/thread/8de4665fa388064d)

Okay, enough of that, but it should be a good start for you guys. :) Onto other things, such as business model:

We will be charging, however, you'll always receive your first 1gb for free. If you need more storage, you'll have to pay. We think the economics of the business lend itself really well to this model and hopefully it'll succeed. We also think it's a pretty fair model which makes us happy, as well. We also have a few other tricks up our sleeves, but we'll see how quickly we get to those. :)

We also support open source a ton, and try to release as much as possible through open source. The ideals of the site (with open APIs, etc) also follow some of the ideas which make open source successful. We think that fostering a large development community will help us to make better software and thereby provide a better service to you, the users.

If any of you are at all interested in developing applications on top of our APIs, I encourage you to join our Google Group:
[http://groups.google.com/group/Openomy-Developers](http://groups.google.com/group/Openomy-Developers)

I hope that helps answer a few questions; I'll be subscribing to this thread and will be back shortly if you have any further questions. Both Maurice and myself will be at RailsConf ([http://www.railsconf.com](http://www.railsconf.com)) this weekend, too, if any of you plan on being there -- we'd love to meet up!

Ian

---

### Post by hanzj on 2006-06-21
Iseff,
Thank you for your input, and welcome to the forums.
I'm a real rookie when it comes to all this (I'm a ex-Windows point-and-click kind of person), and I wonder if it will be much easier if I just use the website ([http://www.openomy.com/filemanager/](http://www.openomy.com/filemanager/)) to upload and download. 

It will be quite troublesome to have to deal with individual files one by one, so I plan on zipping related files up into one package (using archive manager). This way, the number of uploaded files is smaller.  And the number of files I have to download is smaller, too.

Will the speed be slow if we upload/download via the website? If we do it using one of the methods you mentioned, is the speed faster?

Is there a way we can upload via FTP? And if tags can't be added via FTP, it's okay for me. I could add them later via the web interface.

---

### Post by hanzj on 2006-06-21
I have to remember that i can find untagged files (and all files, for that matter) not by searching "*.*", but rather, by [leaving the search box blank.]("http://www.openomy.com/filemanager/search/?searchQuery=&searchForFiles=Search+for+files")

---

### Post by hanzj on 2006-06-21
I tried to upload via the web interface a large file, but before the upload was finished, I got the following message:

------
Sorry, either you have remained inactive for too long a period or never logged in. Please login again.

------------


Oh no! Does that happen after some set time?

---

