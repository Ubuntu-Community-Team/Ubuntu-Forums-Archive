---
title: "Can i unistall compiz-plugins and compiz core"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by nikef on 2008-03-03
Hi 
can i uninstall these safely ,i do not use compiz 

are these needed ? 

thanks for any help

---

### Post by oedha on 2008-03-03
change your visual effect to none first
then sudo apt-get remove compiz
sudo apt-get autoremove
question : why do you want to remove compiz ?

---

### Post by Arthur Archnix on 2008-03-03
You sure can. But after uninstalling, and before rebooting, make sure you change your default window manager.

In a terminal type: gconf-editor

Then search for window_manager and check the box that says key names. This is the one you want: /desktop/gnome/applications/window_manager

Then change the key "default" which says /usr/bin/compiz and make it read instead.. /usr/bin/metacity

This is a per user change though, so you'll need to change this for every user. I'm not sure how to make the change globally.

---

### Post by nikef on 2008-03-03
> **oedha said:**
> change your visual effect to none first
then sudo apt-get remove compiz
sudo apt-get autoremove
question : why do you want to remove compiz ?

Thank you 

i have been having problems for months now,but no1 here could help
my top bar freezes and sometimes my desktop freezes 

my pc was running great until i stupidly activated compiz  :(

so i installed compiz,thinking my pc  would be back to normal ,but its not,i love ubuntu,but have been using xp because of this problem  :(

---

### Post by batonac on 2008-03-04
Try this to turn compiz (or compiz-fusion) off for all users:

Press "Alt-F2" and type "gksu gedit /var/lib/gconf/defaults/%gconf-tree.xml" into the "Run Application" dialog which will appear.

When gedit opens, go to the "Edit" menu, and click on the "Preferences" menu item.

In the dialog which will appear, unselect the "Enable Text Wrapping" option.  Exit the preferences window.

Press "Ctrl-F" and type "window_manager" into the search dialog which will appear.  Press find and then press close.

Scan the document for:

```
                                                <entry name="current" mtime="1204395354" type="schema" stype="string" owner="gnome">
                                                        <local_schema locale="C" short_desc="User window manager (deprecated)">
                                                                <longdesc>
          Window manager to try first.
          This key has been deprecated since GNOME 2.12.
        </longdesc>
                                                        </local_schema>
                                                </entry>
                                                <entry name="default" mtime="1204395354" type="schema" stype="string" owner="gnome">
                                                        <local_schema locale="C" short_desc="Fallback window manager (deprecated)">
                                                                <longdesc>
          Fallback window manager if user window manager can&apos;t be found.
          This key has been deprecated since GNOME 2.12.
        </longdesc>
                                                        </local_schema>
                                                </entry>


```

Replace with this:

```
                                                <entry name="current" mtime="1204395354" type="schema" stype="string" owner="gnome">
                                                        <local_schema locale="C" short_desc="User window manager (deprecated)">
                                                                [B]<default type="string">
                                                                        <stringvalue>/usr/bin/metacity</stringvalue>
                                                                </default>[/B]
                                                                <longdesc>
          Window manager to try first.
          This key has been deprecated since GNOME 2.12.
        </longdesc>
                                                        </local_schema>
                                                </entry>
                                                <entry name="default" mtime="1204395354" type="schema" stype="string" owner="gnome">
                                                        <local_schema locale="C" short_desc="Fallback window manager (deprecated)">
                                                                [B]<default type="string">
                                                                        <stringvalue>/usr/bin/metacity</stringvalue>
                                                                </default>[/B]
                                                                <longdesc>
          Fallback window manager if user window manager can&apos;t be found.
          This key has been deprecated since GNOME 2.12.
        </longdesc>
                                                        </local_schema>
                                                </entry>


```

This is actually the somewhat the same method as described above, but hopefully it will uninstall compiz for all users.

---

