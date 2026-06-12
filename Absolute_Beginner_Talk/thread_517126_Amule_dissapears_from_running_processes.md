---
title: "Amule dissapears from running processes"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Hakker on 2007-08-04
I installed Amule but everytime the program just simply vanishes after a couple of hours to about a day with working.
It just seems to stop running while the amuleweb process keeps on working like it should.

my first question is can it be fixed while keeping it with the gtk gui alive
second could amule be run so that it's just usable by amuleweb (because since amule doesn't run amuleweb is doing nothing)

---

### Post by apswartz on 2007-08-04
I'm not an Amule user, but it is a bittorrent client, right?

Have you thought about using another Torrent client. I use ktorrent without any problems.

---

### Post by Hakker on 2007-08-04
amule is an emule/Kademlia client based on GTK gui instead of normal windows. so no it ain't bittorent. For that I have Torrentflux which does the job nicely.

Seriously I get the idea GTK overloads itself so it just shuts down amule. the amuleweb instance is still running because I mainly use that instead of the gtk interface. so if it can run without the whole gui it would be fine by me as long as I can just remotely add links to it so it will keep going.

---

### Post by Hallvor on 2007-08-05
Try running aMule through the terminal and see what turns up when aMule closes.

---

### Post by Hakker on 2007-08-08
--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    [http://forum.amule.org/board.php?boardid=67](http://forum.amule.org/board.php?boardid=67)
If possible, please try to generate a real backtrace of this crash:
    [http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule 2.1.0 using wxGTK2 v2.6.1 (Unicoded)
Running on: Linux 2.6.15-28-386 i686

[2] ?? in amule [0x80811e3]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.6.so.0[0xb76ae6ea]
[4] ?? in [0xffffe420]
[5] wxStringBase::operator=(wxStringBase const&) in /usr/lib/libwx_baseu-2.6.so.0[0xb7672938]
[6] ?? in amule [0x81fb53b]
[7] ?? in amule [0x81fc30f]
[8] ?? in /usr/lib/libstdc++.so.6 [0xb75ba915]
[9] ?? in /usr/lib/libstdc++.so.6 [0xb75ba94a]
[10] __cxa_rethrow in /usr/lib/libstdc++.so.6[0xb75baa7e]
[11] operator new(unsigned int) in /usr/lib/libstdc++.so.6[0xb75bae81]
[12] operator new[](unsigned int) in /usr/lib/libstdc++.so.6[0xb75baf3d]
[13] ?? in amule [0x820123d]
[14] wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const in /usr/lib/libwx_baseu-2.6.so.0[0xb76222a1]
[15] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.6.so.0[0xb76aa97f]
[16] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.6.so.0[0xb76aab50]
[17] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.6.so.0[0xb76aad01]
[18] wxEvtHandler::ProcessPendingEvents() in /usr/lib/libwx_baseu-2.6.so.0[0xb76ab2d1]
[19] wxAppConsole::ProcessPendingEvents() in /usr/lib/libwx_baseu-2.6.so.0[0xb762256a]
[20] ?? in /usr/lib/libwx_gtk2u_core-2.6.so.0 [0xb780e3a2]
[21] ?? in /usr/lib/libglib-2.0.so.0 [0xb6dc3bf2]
[22] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0xb6dc18d6]
[23] ?? in /usr/lib/libglib-2.0.so.0 [0xb6dc4996]
[24] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0xb6dc4cb8]
[25] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0xb71fb765]
[26] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0xb7827324]
[27] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0xb78b6b2a]
[28] wxAppBase::OnRun() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0xb78b6c0f]
[29] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.6.so.0[0xb7655a44]
[30] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.6.so.0[0xb7655af8]
[31] ?? in amule [0x81276cc]
[32] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb73c9ea2]
[33] __gxx_personality_v0 in amule[0x807dad1]


--------------------------------------------------------------------------------
Aborted

that's the whole error report i get

---

### Post by Hallvor on 2007-08-08
I notice you are using an older version of aMule. The current version is 2.1.3, so you should upgrade to see if it solves the problem.

---

### Post by Hakker on 2007-08-08
well the repository still uses 2.1.0-1ubuntu1

and well I figured those version would be considered as stables

---

### Post by Hallvor on 2007-08-14
That was strange. I believe my version upgraded itself once I enabled the universe and multiverse repositories.

Please upgrade. 2.1.3 is really rock solid.

---

### Post by albert-I on 2007-08-23
I use the 2.1.3 version and dissapers anyway, now I go to see with terminal

> **Hallvor said:**
> That was strange. I believe my version upgraded itself once I enabled the universe and multiverse repositories.

Please upgrade. 2.1.3 is really rock solid.

---

