---
title: "aMule crashes after update"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by x1a4 on 2007-02-25
Hi,

Recently I updated my Xubuntu from the command line like so: 

[I]sudo apt-get update
sudo apt-get dist-upgrade[/I]

(Don't know what was updated because I was surfing the Net on another workspace when it was updating)

Now when I run aMule (version 2.1.3 using wxGTK2 v2.6.3 (Unicoded)) it crashes.  I ran it from the terminal and this is what I got: 

```

Initialising aMule
Checking if there is an instance already running...
No other instances are running.
HTTP download thread started
Loading temp files from /home/x1a4/.aMule/Temp.
Loading PartFile 7 of 7
All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Adding file /home/x1a4/.aMule/Temp/001.part.met to shares
Adding file /home/x1a4/.aMule/Temp/002.part.met to shares
Adding file /home/x1a4/.aMule/Temp/003.part.met to shares
Adding file /home/x1a4/.aMule/Temp/004.part.met to shares
Adding file /home/x1a4/.aMule/Temp/005.part.met to shares
Adding file /home/x1a4/.aMule/Temp/006.part.met to shares
Adding file /home/x1a4/.aMule/Temp/007.part.met to shares
Host: amule.sourceforge.net:80
URL: http://amule.sourceforge.net/lastversion
Response: 200 (Error: 0)
Download size: 6
HTTP download thread ended

Terminated after throwing an instance of 'std::bad_alloc'
        what(): St9bad_alloc
        backtrace:
[2] ?? in /usr/lib/libstdc++.so.6 [0x4d724f55]
[3] ?? in /usr/lib/libstdc++.so.6 [0x4d724f92]
[4] ?? in /usr/lib/libstdc++.so.6 [0x4d7250ca]
[5] operator new(unsigned int) in /usr/lib/libstdc++.so.6[0x4d72550e]
[6] operator new[](unsigned int) in /usr/lib/libstdc++.so.6[0x4d7255ed]
[7] wxWindowBase::GetTitle() const in amule [0x8142180]
[8] wxWindowBase::GetTitle() const in amule [0x81423d8]
[9] wxWindowBase::GetTitle() const in amule [0x8143456]
[10] wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const in /usr/lib/libwx_baseu-2.6.so.0[0x4103f175]
[11] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.6.so.0[0x410ce652]
[12] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.6.so.0[0x410ce79d]
[13] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.6.so.0[0x410ce91f]
[14] wxTimerBase::Notify() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0x4137e471]
[15] ?? in /usr/lib/libwx_gtk2u_core-2.6.so.0 [0x41281175]
[16] ?? in /usr/lib/libglib-2.0.so.0 [0x4d51fdd6]
[17] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0x4d51f802]
[18] ?? in /usr/lib/libglib-2.0.so.0 [0x4d5227df]
[19] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0x4d522b89]
[20] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0x4d9e8574]
[21] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0x41276f9b]
[22] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0x413102ae]
[23] wxAppBase::OnRun() in /usr/lib/libwx_gtk2u_core-2.6.so.0[0x4130f971]
[24] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.6.so.0[0x410749ea]
[25] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.6.so.0[0x41074a96]
[26] CryptoPP::IteratedHash<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, 64u, CryptoPP::HashTransformation>::~IteratedHash() in amule [0x812a500]
[27] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0x4d1d28cc]
[28] __gxx_personality_v0 in amule[0x807cdf1]

Abort (core dumped)
Exit 134

```

Please help.  Thank you.

---

### Post by x1a4 on 2007-02-25
Nevermind, fixed it.  Somehow _amule.conf_ got corrupted.  When I renamed it, aMule started ok.

---

### Post by filogo on 2007-03-28
Same problem for me...something wrong during upgrade...thank you :)

---

