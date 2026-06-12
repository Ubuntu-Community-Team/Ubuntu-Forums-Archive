---
title: "NXserver problem"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by universalerror on 2006-08-09
Hi all, 

I am having a problem with freenx if anyone can help.

I have setup my nxclient on a laptop and another pc that connects to me kubuntu desktop to test them out and it all works fine, but then i goto another office and setup the client and it fails to start the xsession with the following error:


Info: Proxy running in client mode with pid '1012'.
Session: Starting session at 'Wed Aug  9 10:00:38 2006'.
Info: Connecting to remote host '10.8.100.140:5000'.
Info: Connection to remote proxy '10.8.100.140:5000' established.
Warning: Connected to remote NXPROXY version 1.4.0 with local version 2.0.0.
Info: Synchronizing local and remote caches.
Info: Handshaking with remote proxy completed.
Warning: Font server connections not supported by the remote proxy.
Info: Remote proxy doesn't support fake authentication.
Info: Forwarding the real X authorization cookie.
Info: Using wan link parameters 768/24/1/0.
Info: Using cache parameters 4/262144/8192KB/8192KB.
Info: Using image streaming parameters 50/128/1024KB/3072/384.
Info: Using image cache parameters 1/1/32768KB.
Info: Using pack method '16m-jpeg-9' with session 'unix-kde'.
Info: Using ZLIB data compression 1/1/32.
Info: Not using ZLIB stream compression.
Info: No suitable cache file found.
Info: Using remote server '10.8.100.140:5000'.
Session: Session started at 'Wed Aug  9 10:00:38 2006'.
Error: Connection to ':0' failed. Error is 2 'No such file or directory'.
Session: Terminating session at 'Wed Aug  9 10:00:43 2006'.
Info: End of NX transport requested by remote.
Info: Your session was closed before reaching a usable state.
Info: This can be due to the local X server refusing access to the client.
Info: Please check authorization provided by the remote X application.
Info: Shutting down the NX transport.
Session: Session terminated at 'Wed Aug  9 10:00:43 2006'.


Would this be because nxclient only supports 2 users/connections ? even though the is only one connection at any one time ?

if so, how do i remove one connection so that this one will work as it is more important ?

Thanks in advance for the help BTW :)

---

