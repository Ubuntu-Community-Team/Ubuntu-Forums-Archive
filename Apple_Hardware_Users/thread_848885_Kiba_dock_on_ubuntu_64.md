---
title: "Kiba dock on ubuntu 64"
date: 2008-07-03
forum: Apple Hardware Users
---

### Post by RRR-007 on 2008-07-03
I have installed kiba dock as per the below thread on ubuntu 64...

[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)

after the installation, when i type in kiba dock from terminal, got the following error:

** (process:6001): WARNING **: Error (main.c @ line 126):
	Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

	For a core dump, run kiba-dock with --g-fatal-warnings.

I think the above command is looking for kiba dock to the default 32 bit instead of /usr/local/lib64... i have kiba-dock folder under /usr/local/lib64...

How do i start the kiba-dock from terminal, also i tried from Applications->Accessories->Kiba dock... nothing has been displayed when i click kiba dock, but kiba dock settings was popped up.

can someone plz tell me how to start kiba dock after all the above installations... i wanna give the dock effect to ubuntu just as one in my mac os... thanks in advance.

---

### Post by cyberdork33 on 2008-07-03
I am running 64bit but have no /usr/local/lib64 Are you sure that is right?

If you want to specify a different path, use the parameter mentioned...
```
kiba-dock --plugin-path /usr/local/lib64
```

---

### Post by RRR-007 on 2008-07-04
you are right, there is no /usr/local/lib64 folder. i ran the command suggested and have got the following warnings and error, but dock has been displayed with problems that if i close the terminal, it is also vanishing from desktop....

~$ kiba-dock --plugin-path /usr/lib64/kiba-dock

** (kiba-dock:5911): WARNING **: Error (plugin.c @ line 289):
	Failed to load plugin at '/usr/lib64/kiba-dock/dock_plugins/libdbus.so': The plugin can only be loaded once!

	For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:5911): WARNING **: Error (plugin.c @ line 289):
	Failed to load plugin at '/usr/lib64/kiba-dock/dock_plugins/liblauncher.so': The plugin can only be loaded once!

	For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:5911): WARNING **: Error (plugin.c @ line 289):
	Failed to load plugin at '/usr/lib64/kiba-dock/dock_plugins/libtrash.so': The plugin can only be loaded once!

	For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:5911): WARNING **: Error (plugin.c @ line 289):
	Failed to load plugin at '/usr/lib64/kiba-dock/dock_plugins/libdbus.so': The plugin can only be loaded once!

	For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:5911): WARNING **: Error (plugin.c @ line 289):
	Failed to load plugin at '/usr/lib64/kiba-dock/dock_plugins/liblauncher.so': The plugin can only be loaded once!

	For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:5911): WARNING **: Error (plugin.c @ line 289):
	Failed to load plugin at '/usr/lib64/kiba-dock/dock_plugins/libtrash.so': The plugin can only be loaded once!

	For a core dump, run kiba-dock with --g-fatal-warnings.

Also the dock is static i.e when i mouse over the icons it remains same and it doesn't appear to be magnified as in mac, i think that i need to enable some setting in kiba settings but i dont know what was that....

Also I wanted this dock to be started when i log on to ubuntu, so i added kiba-dock in startup programs (system-preference-session) but of no luck... i entered only the kiba-dock command in startup program, let me try with the command that you suggested  but why i'll have to specify the path and why it is not detecting automatically like any other apps...

---

