---
title: "amule 2.1.3 can not connect"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by slobodan on 2007-11-12
I have a problem with amule  2.1.3 it fails to download serverlist  and it doesn't want to connect.. Here's the console output:
bobi@deus:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Loading temp files from /home/bobi/.aMule/Temp.

All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /home/bobi/.aMule/Incoming/ shared
HTTP download thread started
HTTP download thread ended
HTTP download thread started
HTTP download thread ended
HTTP download thread started
HTTP download thread ended
HTTP download thread started

--------------------------------------------------------------------------------
A fatal error has occurred and aMule has crashed.
Please assist us in fixing this problem by posting the backtrace below in our
'aMule Crashes' forum and include as much information as possible regarding the
circumstances of this crash. The forum is located here:
    [http://forum.amule.org/board.php?boardid=67](http://forum.amule.org/board.php?boardid=67)
If possible, please try to generate a real backtrace of this crash:
    [http://www.amule.org/wiki/index.php/Backtraces](http://www.amule.org/wiki/index.php/Backtraces)

----------------------------=| BACKTRACE FOLLOWS: |=----------------------------
Current version is: aMule 2.1.3 using wxGTK2 v2.8.4 (Unicoded)
Running on: Linux 2.6.22-14-generic i686

[2] wxThreadHelperThread::~wxThreadHelperThread() in amule [0x8082b0b]
[3] wxFatalSignalHandler in /usr/lib/libwx_baseu-2.8.so.0[0xb768d5d6]
[4] ?? in [0xffffe420]
[5] wxGIFDecoder::GetFrameSize(unsigned int) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb794f392]
[6] wxGIFDecoder::ConvertToImage(unsigned int, wxImage*) const in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb794f3fc]
[7] wxTextCtrl::wxTextCtrl() in amule [0x8236add]
[8] wxAppConsole::HandleEvent(wxEvtHandler*, void (wxEvtHandler::*)(wxEvent&), wxEvent&) const in /usr/lib/libwx_baseu-2.8.so.0[0xb75e0ee5]
[9] wxEvtHandler::ProcessEventIfMatches(wxEventTableEntryBase const&, wxEvtHandler*, wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0xb76890af]
[10] wxEventHashTable::HandleEvent(wxEvent&, wxEvtHandler*) in /usr/lib/libwx_baseu-2.8.so.0[0xb76891fd]
[11] wxEvtHandler::ProcessEvent(wxEvent&) in /usr/lib/libwx_baseu-2.8.so.0[0xb7689366]
[12] wxTimerBase::Notify() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb799ab71]
[13] ?? in /usr/lib/libwx_gtk2u_core-2.8.so.0 [0xb7876e55]
[14] ?? in /usr/lib/libglib-2.0.so.0 [0xb70048d6]
[15] g_main_context_dispatch in /usr/lib/libglib-2.0.so.0[0xb700411c]
[16] ?? in /usr/lib/libglib-2.0.so.0 [0xb700755f]
[17] g_main_loop_run in /usr/lib/libglib-2.0.so.0[0xb7007909]
[18] gtk_main in /usr/lib/libgtk-x11-2.0.so.0[0xb6d9a9e4]
[19] wxEventLoop::Run() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb786d7cc]
[20] wxAppBase::MainLoop() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb790f00e]
[21] wxAppBase::OnRun() in /usr/lib/libwx_gtk2u_core-2.8.so.0[0xb790e601]
[22] wxEntry(int&, wchar_t**) in /usr/lib/libwx_baseu-2.8.so.0[0xb761d25a]
[23] wxEntry(int&, char**) in /usr/lib/libwx_baseu-2.8.so.0[0xb761d307]
[24] CryptoPP::IteratedHash<unsigned int, CryptoPP::EnumToType<CryptoPP::ByteOrder, 0>, 64u, CryptoPP::HashTransformation>::~IteratedHash() in amule [0x812d010]
[25] __libc_start_main in /lib/tls/i686/cmov/libc.so.6[0xb733d050]
[26] wxNotebook::SetPadding(wxSize const&) in amule[0x807ee51]


--------------------------------------------------------------------------------
Aborted (core dumped)
bobi@deus:~$ 

thanks
Slobodan

---

### Post by Paul820 on 2007-11-12
**e**Mule runs in wine.

---

### Post by slobodan on 2007-11-12
I guess I will have to install wine since MLDonkey doesn't work too.

thanks
Slobodan

---

### Post by ron999 on 2007-11-12
Hi
aMule 2.1.3 is working fine for me in Feisty.
This is the whole output from my console:-

ron@ron-desktop:~$ amule
Initialising aMule
Checking if there is an instance already running...
No other instances are running.
Loading temp files from /home/ron/.aMule/Temp.

All PartFiles Loaded.
ListenSocket: Ok.

External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672


******************
So mine is similar to yours except that I see from your report that it says:-
**Empty dir /home/bobi/.aMule/Incoming/ shared**
My output doesn't have a line like that.

I've looked in my .aMule/Incoming folder and there isn't a sub-folder named "shared". No sub-folders at all.
(You need to view /.aMule with 'show hidden files' ticked).
Are you sure that you do have a sub-folder named "shared"?
Perhaps you are trying to download into a non-existent folder.
There's settings in Preferences > Directories > Incoming Directory
:cool:

---

### Post by ruibernardo on 2007-11-12
I agree with ron999. 

Just to note that the error might be happening because of the space in the " shared" folder. Try to rename that folder, update aMule preferences and restart aMule.

---

### Post by meho_r on 2007-11-17
Similar problem here on Gutsy. It seems that you can't get rid of 'empty shared' folder. Changing dirs in Preferences doesn't help :( And when trying to get list of servers Amule simply crashes. Bug?

---

### Post by kamitsukai on 2007-11-17
same problem on my gutsy install *goes and installs emule in wine*

---

### Post by Festor on 2007-11-18
Try with aMule 2.20 CVS

[http://forum.amule.org/index.php?topic=13700.0](http://forum.amule.org/index.php?topic=13700.0)

---

### Post by slobodan on 2007-11-23
Wine + eMule combination works great :popcorn:, highly recommended.  Maybe I should try to make amule work, or check some cvs version, but since Ubuntu 7.10 I have a very high standards that everything should just work, and work really great. :) 

Slobodan

---

### Post by hyper_ch on 2007-11-23
why not just creating that " shared" folder? maybe even symlinking to a "shared" one?

And after directories have changed, you need to restart amule for the changes to come in effect.

---

### Post by blackdog7 on 2008-01-10
I have the same problem on Gutsy.
If I make the " shared" directory, will nothing changed as shown followed:
External connections disabled in config file
*** Server UDP socket (TCP+3) at 0.0.0.0:4665
*** TCP socket (TCP) listening on 0.0.0.0:4662
*** Client UDP socket (extended eMule) at 0.0.0.0:4672
Empty dir /home/bobi/.aMule/Incoming/ shared

Any other idea? above wine + emule...

---

### Post by blackdog7 on 2008-01-10
I don't believe that!

Now the amule works for me!
1. First I have deleted all of server in the list.
2. Next I have added manually the following entry (i think the best server):
Razorback 3.1 - 193.138.205.25:5000
3. Connect - and enjoy! :)

That was!

---

