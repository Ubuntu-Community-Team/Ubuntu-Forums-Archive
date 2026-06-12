---
title: "hellanzb and a few other questions"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by IsleOf on 2007-06-02
Hello again. Finally getting a chance to play with Ubuntu again.

Ive installed and configured hellanzb. But im not exactly sure how to get it running once i find an nzb i want from newzbin? can anyone help?

Secondly how would i 'detach hardware' as in remove a usb key?

Thirdly. Ubuntu appearance is pretty plain and blocky the way it is. How do i improve it and mak it look better

---

### Post by godd4242 on 2007-06-02
> **IsleOf said:**
> Hello again. Finally getting a chance to play with Ubuntu again.

Ive installed and configured hellanzb. But im not exactly sure how to get it running once i find an nzb i want from newzbin? can anyone help?

Secondly how would i 'detach hardware' as in remove a usb key?

Thirdly. Ubuntu appearance is pretty plain and blocky the way it is. How do i improve it and mak it look better

Well I don't know what newzbin is but I'll look into it in a moment.

To safely detach a USB key, go to "Places" or "Home" and right click on the USB drive on the little list of mounted drives on your left. Hit UnMount, and you'll be fine.

And now onto making Ubuntu pretty:

Beryl will make your computer look absolutely stunning, and Emerald theme manager is a great way to make your windows look different and "exciting."

warning is, Beryl will (most likely) make you wanna kill yourself because it's so damned hard to get working.

[http://ubuntuforums.org/showthread.php?t=349732](http://ubuntuforums.org/showthread.php?t=349732)

That's a good starting point.


After that, look into Avant Window manager, Kiba-Dock, and Screenlets. (all beta and deliciously buggy)

If working on all those sounds like too much work, you can pretty much customize your existing "base" Ubuntu desktop just by clicking on one of the panels (the place where it says apps places system, or lists the windows open) and hit properties. From there you can adjust size, make them autohide, change color, load photos as backgrounds, add drawers notepads search functions.

Lots of stuff.


ahhh I forgot I forgot. 
Go to System > Preferences > themes to mix up your basic Ubuntu themes.

Go to System > preferences > Desktop effects to turn on compiz, which allows you to have the "desktop cube" and windows that shake when you move them around, kinda like Jello.

---

### Post by IsleOf on 2007-06-02
Cheers for that

newzbin is [www.newzbin.com](www.newzbin.com). Just a website to get nzbs. i dont use newsgroups i just download from them. in windows i would get nzb files from newzbin and use grabit.

Beryl does look great but was waiting until i get more experience and the computer doing what i need it to be doing before diving into it.

---

### Post by IsleOf on 2007-06-02
This is whats in terminal when i run hellanzb but dont actually know how to get it to run the nzbs.

```
aaron@aaron-desktop:~$ hellanzb

hellanzb v0.10 (config = /etc/hellanzb.conf)
(changeme) Opening 4 connections...
hellanzb - Now monitoring queue...
```


This is the hellanzb config if thats any use

```
# 
# hellanzb.conf - sample hellanzb configuration file
#
# To quickly get started, change the default defineServer() call and the
# Hellanzb.PREFIX_DIR directory
#
# This is actually interpreted python code: strings must be surrounded by
# quotes, numbers and the 'None' keyword should not
# 
# $Id: hellanzb.conf.sample 801 2006-07-27 04:11:01Z alex $

# Log output to this file, set to None (no single quotes) for no logging
Hellanzb.LOG_FILE = '/var/tmp/hellanzb.log'

# Uncomment this line to log DEBUG messages to the specified file
#Hellanzb.DEBUG_MODE = '/var/tmp/hellanzb-debug.log'

# Automatically roll over both log files when they reach LOG_FILE_MAX_BYTES
# size
Hellanzb.LOG_FILE_MAX_BYTES = 0

# Save LOG_FILE_BACKUP_COUNT of those rolled over log files
Hellanzb.LOG_FILE_BACKUP_COUNT = 0


# Define server connections. Servers can have multiple hosts, hellanzb will
# persist the number of connections to each specified server. There may be
# multiple defineServer lines.

# Set both the username and password to 'None' (without the quotes) if your
# usenet server does not require authorization
defineServer(id = 'changeme',
             hosts = [ 'unlimited.newhosting.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = '**********',
             password = '**********',
             #username = None,           # no auth
             #password = None,

             connections = 4,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds, 0 to disable
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )

# Uncomment this line to limit all server connections to the specified KB/s
# bandwidth
#Hellanzb.MAX_RATE = 150 # limit to 150kB/s


# Important locations
Hellanzb.PREFIX_DIR = os.path.expanduser('~') + '/.hellanzb/'

# Where to put queued .nzb files
Hellanzb.QUEUE_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.queue/'

# Where the fully processed archives go
Hellanzb.DEST_DIR = Hellanzb.PREFIX_DIR + 'done/'

# The .nzb currently being downloaded is stored here
Hellanzb.CURRENT_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.current/'

# The archive currently being downloaded is stored here
Hellanzb.WORKING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.working/'

# Archives interrupted in the middle of downloading are stored here temporarily
Hellanzb.POSTPONED_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.postponed/'

# Archives currently being processed. May contains archive directories, or
# symbolic links to archive directories
Hellanzb.PROCESSING_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.processing/'

# Temp storage
Hellanzb.TEMP_DIR = Hellanzb.PREFIX_DIR + 'nzb/daemon.temp/'

# Filename to store hellanzb state in between CTRL-Cs. The state (includes the
# order of the queue, and smart par recovery information) is intermittently
# written out as XML to this file
Hellanzb.STATE_XML_FILE = Hellanzb.PREFIX_DIR + 'nzb/hellanzbState.xml'


# _Sub directory within the nzb archive dir_ to move processed files to
Hellanzb.PROCESSED_SUBDIR = 'processed'

# Remove the PROCESSED_SUBDIR if the archive was successfully post processed. 
# Warning: The normal Hellanzb.LOG_FILE should be enabled with this option --
# for a record of what hellanzb deletes
Hellanzb.DELETE_PROCESSED = True

# Disable SMART_PAR (download all PAR files)
#Hellanzb.SMART_PAR = False

# Supply a path to the (un)rar command
#Hellanzb.UNRAR_CMD = None

# Supply a path to the par2 command
Hellanzb.PAR2_CMD = '/usr/bin/par2'

# Skip unraring during post processing
Hellanzb.SKIP_UNRAR = True

# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
#Hellanzb.UMASK = 0022


# Supported music types (case insensitive) and optionally their decompression
# executables
# and the file type that executable will decompress to (case insensitive). The
# exes must be in the PATH.
#
# <FILE> will be replaced with the name of music file
# optional <DESTFILE> is <FILE> with the specified extension
#
# None means these files don't need to be decompressed
defineMusicType('wav', None, None)
defineMusicType('mp3', None, None)
#defineMusicType('ape', 'mac <FILE> <DESTFILE> -d', 'wav')
#defineMusicType('flac', 'flac -d -- <FILE>', 'wav')
#defineMusicType('shn', 'shorten -x < <FILE> > <DESTFILE>', 'wav')

# Max files we should decompress at the same time
Hellanzb.MAX_DECOMPRESSION_THREADS = 2


# Enable Mac OS X Growl notifications
Hellanzb.GROWL_NOTIFY = False

# The growl notification server, in the format 'hostname'
Hellanzb.GROWL_SERVER = 'IP'

# The growl password
Hellanzb.GROWL_PASSWORD = 'password'


# Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'


# Username/Password to http://www.newzbin.com for automatic NZB downloading
Hellanzb.NEWZBIN_USERNAME = '*******i'	
Hellanzb.NEWZBIN_PASSWORD = '********'


# If any of the following file types are missing from the archive and cannot be
# repaired, continue processing because they're unimportant (case insensitive)
Hellanzb.NOT_REQUIRED_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]

# Don't get rid of (move into the PROCESSED dir) the following file types when
# finished post processing (case insensitive)
#Hellanzb.KEEP_FILE_TYPES = [ 'log', 'm3u', 'nfo', 'nzb', 'sfv', 'txt' ]
Hellanzb.KEEP_FILE_TYPES = [ 'nfo', 'txt' ]


# List of alternative file extensions matched as NZB files in the QUEUE_DIR.
# The 'nzb' file extension is always matched
#Hellanzb.OTHER_NZB_FILE_TYPES = [ 'xml' ]

# Delay enqueueing new, recently modified NZB files added to the QUEUE_DIR until
# this many seconds have passed since the NZB's last modification time (defaults
# to 10 seconds)
#Hellanzb.NZBQUEUE_MDELAY = 10

# Optional external handler script. hellanzb will run this script after post
# processing an archive, with the following arguments:
#
# handler_script type archiveName destDir elapsedTime parMessage
#
# type: post processing result, either 'SUCCESS' or 'ERROR'
# archiveName: name of the archive, e.g. 'Usenet_Post5'
# destDir: where the archive ended up, e.g. '/ext2/usenet/Usenet_Post5'
# elapsedTime: a pretty string showing how long post processing took, e.g.
#              '10m 37s'
# parMessage: optional post processing message. e.g. '(No Pars)'
#Hellanzb.EXTERNAL_HANDLER_SCRIPT = '~/bin/post_hellanzb.sh'
```

Ive replaced my usernames and passwords with *******

---

### Post by tehkain on 2007-06-03
Assuming you installed from the repos.

Go into your file browser and navigate to the hidden folder(. in front of a folder means hidden):
/home/(username)/.hellanzb/nzb/daemon.queue  is where you place your NZBs
/home/(username)/.hellanzb/done is where your finished downloads are placed

Assuming you want to run hellanzb in the background you can run the command 'hellanzb -D'. It will run in daemon mode. To find all the controls run 'man hellanzb' and look at the remote calls.

Also do a "sudo apt-get install unrar" then mod your config file from

#Hellanzb.UNRAR_CMD = None
to
Hellanzb.UNRAR_CMD = '/usr/bin/unrar'

and 

Hellanzb.SKIP_UNRAR = True
to
Hellanzb.SKIP_UNRAR = False

---

