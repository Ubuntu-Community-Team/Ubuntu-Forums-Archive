---
title: "Help me get this to work"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by BurgesS on 2007-05-21
I can't remember how I originally got this thing to work but I haven't been able to get it to work since I upgraded.  It is a small perl script that changes my wallpaper every time it runs.  I had set up a cron job to run it at boot every time.

I can run the program manually from the desktop but if I try to copy it into any other directory it won't work.

Here is the code:

```
#!/usr/bin/env python

from xml.dom import minidom
import gconf
import os
import random

client = gconf.client_get_default()

def decodeWP(node):
	results = {}
	for value in node.childNodes:
		if value.nodeType==1:
			ndata = ''
			for val in value.childNodes:
                                if val.nodeType==3: # TEXT_NODE
                                        ndata = ndata + val.data
			results[value.tagName] = ndata
	return results;

settings = os.path.expanduser('~') + '/.gnome2/backgrounds.xml'
xmldoc = minidom.parse(settings)

wallpapers = [];
for child in xmldoc.childNodes:
	if child.nodeType==1:
		if child.tagName=='wallpapers':
			for wp in child.childNodes:
				if wp.nodeType==1:
					if wp.tagName=='wallpaper':
						wallpapers.append(decodeWP(wp))

random.seed()
index = random.randint(0, len(wallpapers)-1)
changeSet = gconf.ChangeSet()

wp = wallpapers[index]
gs = '/desktop/gnome/background/'

print 'Setting background to: ' + wp['name']
changeSet.set_string(gs + 'picture_filename',   wp['filename'])
changeSet.set_string(gs + 'picture_options',    wp['options'])
changeSet.set_string(gs + 'primary_color',      wp['pcolor'])
changeSet.set_string(gs + 'secondary_color',    wp['scolor'])
changeSet.set_string(gs + 'color_shading_type', wp['shade_type'])

client.commit_change_set(changeSet, True)

```

Thanks for the help.

---

### Post by jargoman on 2007-05-21
I'm not a perl script writer myself but no one answered you yet so I might as well.

When you say it doesn't work do you mean it won't copy to another place or won't run once there.
Either way make sure you have the right permitions. Also when you copy to a new location some times you have to remark the script as executable.

$ sudo cp /home/user/Desktop/name-of-script /new-path-to-script
$ chmod a+x path-to-script/name-of-script

or is it possible to write another script somewhere else that will in turn run this one. You might be able to rename your script with . infront to mark it hidden

---

### Post by BurgesS on 2007-05-21
Actually I said perl I meant python.  I think the trouble I was having was coming up with the proper entry in my crontab file instead of  program itself.  That is how I was running it before but now I can't get it to run with cron.  I have been editing the crontab file for a couple of hours and can't get it to work.

I finally gave up and added it to the session manager and it works fine.  I just hate not being able to get something to work when I know it should.

---

