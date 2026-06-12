---
title: "Hawaii Desktop Environment 0.1.92 Released!"
date: 2013-08-12
forum: Any Other OS
---

### Post by Gnawnsense on 2013-08-12
Hello everyone!

As a minor [Maui Project]("http://www.maui-project.org") contributor, I was extremely excited to see some of the progress that's been made over this way in regards to the Hawaii Desktop Environment that will be used for Maui. Pier posted up a YouTube video today to show off the progress that's been made.

[https://www.youtube.com/watch?v=8_pR9FDDnjw](https://www.youtube.com/watch?v=8_pR9FDDnjw)

> [INDENT]   Hawaii Shell is now in a very good shape, it has the most important things a shell needs:
      
[LIST]
[*]Application launcher
[*]Panels
[*]PolicyKit integration
[*]Notifications
[*]Lock screen
[/LIST]
 More features will come from here to Hawaii 0.2.0.
 [/INDENT]


---

### Post by cecilpierce on 2013-08-12
Looks very nice ! 

Is the installable iso about ready ?

I have Maui running in Arch, Thanks.

---

### Post by mikodo on 2013-08-12
> **cecilpierce said:**
> Looks very nice ! 

Is the installable iso about ready ?

I have Maui running in Arch, Thanks.

Isn't the .iso available here. At the right in green?

[http://www.maui-project.org/en/download/](http://www.maui-project.org/en/download/)

From clicking on the download at the bottom of this page. (It didn't redirect for me on first try).

[http://www.maui-project.org/](http://www.maui-project.org/)

---

### Post by cecilpierce on 2013-08-12
> **mikodo said:**
> Isn't the .iso available here. At the right in green?

[http://www.maui-project.org/en/download/](http://www.maui-project.org/en/download/)

From clicking on the download at the bottom of this page. (It didn't redirect for me on first try).

[http://www.maui-project.org/](http://www.maui-project.org/)

That download is a live only to try it, Pier said he was making a DVD that could be installed to hard drive,
should be out soon I hope!

---

### Post by Gnawnsense on 2013-08-12
Announcement on the mailing lists earlier:

> "[FONT=arial]Hello everyone,[/FONT]

[FONT=arial]The first public snapshot of Hawaii Shell is available.[/FONT][FONT=arial]
This release is limited to Hawaii Shell and the Weston plugin not the whole desktop.

The strategy is to release one module at a time.

For this release 30 issues were closed [1] and there are 215 commits between 0.1.0 and 0.1.92 [2] and 25 commits for the Weston plugin [3].
[/FONT]
[FONT=arial]
A lot of progress were made in the last couple of months, including:

 - Improved multi screen support
 - Theming QML API
 - A lot of glitches in the AppChooser fixed
 - Modal dialogs
 - Lock screen
 - Logout, lock, restart, power off and suspend actions

Themes can be written using QML which is a lot easier than the previous approach inherited from Plasma involving SVG images.
The default theme is builtin for now, for 0.2.0 I plan to make external themes loadable but there's no API stability promise yet.

You can build Hawaii sources from git. [4][/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Make sure you build qtwayland stable branch and revert 10652f8dd675aa0d12c11597c165831c8ba0b8b4 otherwise you won't see icons.

If you are running Archlinux there are binary packages available. [5]

Hawaii Shell is now in a very good shape, it has the most important things a shell needs:

 - Application launcher
 - Panels
 - PolicyKit integration
 - Notifications
 - Lock screen

More features will come from here to Hawaii 0.2.0.[/FONT]
[FONT=arial]
Thus I am going to use Hawaii everyday at home, to better spot issues.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Mandatory video is here: [https://www.youtube.com/watch?v=8_pR9FDDnjw](https://www.youtube.com/watch?v=8_pR9FDDnjw)

[1] [https://github.com/hawaii-desktop/shell/issues?milestone=2&page=1&state=closed](https://github.com/hawaii-desktop/shell/issues?milestone=2&page=1&state=closed)
[/FONT]
[FONT=arial][2] [https://github.com/hawaii-desktop/shell/compare/v0.1.0...v0.1.92](https://github.com/hawaii-desktop/shell/compare/v0.1.0...v0.1.92)[/FONT]
[FONT=arial][3] [https://github.com/hawaii-desktop/shell-weston-plugins/compare/v0.1.90...v0.1.92](https://github.com/hawaii-desktop/shell-weston-plugins/compare/v0.1.90...v0.1.92)
[4] [https://github.com/hawaii-desktop/hawaii](https://github.com/hawaii-desktop/hawaii)
[5] [http://www.maui-project.org/download](http://www.maui-project.org/download)[/FONT]

---

### Post by NormanFLinux on 2013-08-12
Looks like its not even a beta.

A complete desktop environment is needed for testing.

Without it, its just desktop vaporware.

---

### Post by Gnawnsense on 2013-08-12
> **NormanFLinux said:**
> Looks like its not even a beta.

A complete desktop environment is needed for testing.

Without it, its just desktop vaporware.

We're simply letting people know progress is being made; we had another thread floating around and people asked to be kept updated.
 
Regarding your assumption regarding the project being vaporware, I'm inclined to disagree with the statement. You can easily check out the released modules thus far for Hawaii and check out Maui thus far on a Live CD with no issues. Nothing has been announced with nothing to show or made available to the public and there has been no developmental delays, and the process is completely transparent. 

Like always, you're more than welcome to stop by the mailing list and IRC and see what else is being worked on that's not readily available to the public yet.

We do appreciate you taking the time to stop by, though. Hopefully we'll make some progress that will pique your interest towards Hawaii and Maui.

---

### Post by NormanFLinux on 2013-08-13
I do wish your project the best.

But I do think reviewers want to see something that they can compare against current distros.

Keep us updated on your progress!

---

### Post by SBMN7 on 2013-08-16
hi, i have ubuntu 11.10 now. may i install this desktop environment in my system ? inter celeron 2.2ghz, 1 gb ram. msi board. please reply, then i will download it.

---

### Post by cecilpierce on 2013-08-16
> **SBMN7 said:**
> hi, i have ubuntu 11.10 now. may i install this desktop environment in my system ? inter celeron 2.2ghz, 1 gb ram. msi board. please reply, then i will download it.

The download is live 64bit only, no install yet.
There is instructions on how to run it with Arch Linux, its also 64bit only.

---

### Post by hellnest2 on 2013-08-16
This one sounds internesting... gonna check it out soon ^^

---

### Post by cecilpierce on 2013-08-19
Works good...:P

---

