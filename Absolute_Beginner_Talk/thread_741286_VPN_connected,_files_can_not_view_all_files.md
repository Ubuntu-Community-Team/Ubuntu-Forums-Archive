---
title: "VPN connected, files can not view all files"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by english on 2008-03-31
Hi all

Absolutely loving Ubuntu but I cannot view files over VPN I get the following message box: -
 
      The folder contents could not be displayed.
      Sorry, couldn't display all the contents of "d_drive"

I enclose the relevant section of my sys log file with made up IP adds for security reasons

Mar 31 21:15:40 jons-laptop NetworkManager: <info>  Will activate VPN connection 'work', service 'org.freedesktop.NetworkManager.ppp_starter', user_name 'jonathan', vpn_data 'ppp-connection-type / pptp / pptp-remote / vpn-xxxxxxxxxxxx.dyndns.org / usepeerdns / yes / encrypt-mppe / no / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / yes / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / no / usepeerdns-overtunnel / yes / routes / 192.168.x.xx/24 / use-routes / yes', route '192.168.x.xx/24'. 
Mar 31 21:15:40 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 2 of 4 (Connection Prepare Wait) scheduled... 
Mar 31 21:15:40 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 2 of 4 (Connection Prepare Wait) waiting... 
Mar 31 21:15:40 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 2 of 4 (Connection Prepare Wait) complete. 
Mar 31 21:15:40 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 3 of 4 (Connect) scheduled... 
Mar 31 21:15:40 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 3 of 4 (Connect) sending connect request. 
Mar 31 21:15:40 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 3 of 4 (Connect) request sent, waiting for reply... 
Mar 31 21:15:40 jons-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3. 
Mar 31 21:15:41 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 3 of 4 (Connect) reply received. 
Mar 31 21:15:41 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 4 of 4 (IP Config Get) timeout scheduled... 
Mar 31 21:15:41 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 3 of 4 (Connect) complete, waiting for IP configuration... 
Mar 31 21:15:41 jons-laptop pppd[7473]: Plugin nm-pppd-plugin.so loaded.
Mar 31 21:15:41 jons-laptop pppd[7473]: nm-pppd-plugin: plugin initialized.
Mar 31 21:15:41 jons-laptop pppd[7474]: pppd 2.4.4 started by root, uid 0
Mar 31 21:15:41 jons-laptop pppd[7474]: Using interface ppp0
Mar 31 21:15:41 jons-laptop pppd[7474]: Connect: ppp0 <--> /dev/pts/0
Mar 31 21:15:41 jons-laptop pptp[7477]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated 
Mar 31 21:15:41 jons-laptop pptp[7479]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request' 
Mar 31 21:15:41 jons-laptop pptp[7479]: anon log[ctrlp_disp:pptp_ctrl.c:738]: Received Start Control Connection Reply
Mar 31 21:15:41 jons-laptop pptp[7479]: anon log[ctrlp_disp:pptp_ctrl.c:772]: Client connection established.
Mar 31 21:15:42 jons-laptop pppd[7474]: nm-pppd-plugin: CHAP check hook.
Mar 31 21:15:42 jons-laptop pptp[7479]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request' 
Mar 31 21:15:42 jons-laptop pptp[7479]: anon log[ctrlp_disp:pptp_ctrl.c:857]: Received Outgoing Call Reply.
Mar 31 21:15:42 jons-laptop pptp[7479]: anon log[ctrlp_disp:pptp_ctrl.c:896]: Outgoing call established (call ID 0, peer's call ID 1009). 
Mar 31 21:15:42 jons-laptop pptp[7479]: anon log[ctrlp_disp:pptp_ctrl.c:949]: PPTP_SET_LINK_INFO received from peer_callid 8
Mar 31 21:15:42 jons-laptop pptp[7479]: anon log[ctrlp_disp:pptp_ctrl.c:952]:   send_accm is 00000000, recv_accm is FFFFFFFF
Mar 31 21:15:42 jons-laptop pptp[7479]: anon warn[ctrlp_disp:pptp_ctrl.c:955]: Non-zero Async Control Character Maps are not supported!
Mar 31 21:15:42 jons-laptop pppd[7474]: nm-pppd-plugin: CHAP credentials requested.
Mar 31 21:15:42 jons-laptop pppd[7474]: CHAP authentication succeeded
Mar 31 21:15:45 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 12 (expecting 8, lost or reordered)
Mar 31 21:15:45 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 13 (expecting 8, lost or reordered)
Mar 31 21:15:45 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 14 (expecting 8, lost or reordered)
Mar 31 21:15:45 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 15 (expecting 8, lost or reordered)
Mar 31 21:15:48 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 17 (expecting 16, lost or reordered)
Mar 31 21:15:48 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 18 (expecting 16, lost or reordered)
Mar 31 21:15:50 jons-laptop pppd[7474]: MPPE 128-bit stateless compression enabled
Mar 31 21:15:53 jons-laptop pppd[7474]: Cannot determine ethernet address for proxy ARP
Mar 31 21:15:53 jons-laptop pppd[7474]: local  IP address 192.168.x.xx
Mar 31 21:15:53 jons-laptop pppd[7474]: remote IP address 192.168.x.xx
Mar 31 21:15:53 jons-laptop pppd[7474]: primary   DNS address 127.0.0.1
Mar 31 21:15:53 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 4 of 4 (IP Config Get) reply received. 
Mar 31 21:15:54 jons-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
Mar 31 21:15:54 jons-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Mar 31 21:15:54 jons-laptop NetworkManager: <info>  VPN Activation (work) Stage 4 of 4 (IP Config Get) complete. 
Mar 31 21:15:54 jons-laptop NetworkManager: <info>  VPN Activation (work) successful. 
Mar 31 21:15:54 jons-laptop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 4. 
Mar 31 21:16:45 jons-laptop pptp[7479]: anon log[logecho:pptp_ctrl.c:676]: Echo Request received.
Mar 31 21:16:45 jons-laptop pptp[7479]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply' 
Mar 31 21:16:45 jons-laptop pptp[7479]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Mar 31 21:16:52 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 31 (expecting 30, lost or reordered)
Mar 31 21:17:01 jons-laptop /USR/SBIN/CRON[7534]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 31 21:17:12 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 33 (expecting 32, lost or reordered)
Mar 31 21:18:02 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 40 (expecting 34, lost or reordered)
Mar 31 21:18:05 jons-laptop pptp[7479]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Mar 31 21:18:22 jons-laptop pptp[7477]: anon log[decaps_gre:pptp_gre.c:407]: buffering packet 43 (expecting 41, lost or reordered)
Mar 31 21:19:05 jons-laptop pptp[7479]: anon log[logecho:pptp_ctrl.c:676]: Echo Reply received.
Mar 31 21:20:52 jons-laptop pppd[7474]: No response to 10 echo-requests
Mar 31 21:20:52 jons-laptop pppd[7474]: Serial link appears to be disconnected.
Mar 31 21:20:52 jons-laptop pppd[7474]: Connect time 5.0 minutes.
Mar 31 21:20:52 jons-laptop pppd[7474]: Sent 0 bytes, received 32 bytes.
Mar 31 21:20:52 jons-laptop pppd[7474]: MPPE disabled
Mar 31 21:20:55 jons-laptop pppd[7474]: Connection terminated.
Mar 31 21:20:55 jons-laptop pptp[7477]: anon warn[decaps_hdlc:pptp_gre.c:197]: short read (-1): Input/output error
Mar 31 21:20:55 jons-laptop pptp[7477]: anon warn[decaps_hdlc:pptp_gre.c:209]: pppd may have shutdown, see pppd log
Mar 31 21:20:55 jons-laptop pptp[7479]: anon log[callmgr_main:pptp_callmgr.c:231]: Closing connection (unhandled)
Mar 31 21:20:55 jons-laptop pptp[7479]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request' 
Mar 31 21:20:55 jons-laptop pptp[7479]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Mar 31 21:20:55 jons-laptop pppd[7474]: Modem hangup
Mar 31 21:20:55 jons-laptop pppd[7474]: Exit.

Please help I would so love to not have to log into windows (dirty word) ever again.

many thanks in advance

English

PS I have trawled through previous threads and did everything I understood didn't understand all so didn't do anything - It left me dazed and confused so sorry if this is a repeat of a previous thread

---

### Post by cmnorton on 2008-03-31
How did you configure the VPN? What kind is it?

I use pppoe and connect through Network Manager. 

Try setting your MTU down around 1404.

---

### Post by english on 2008-03-31
hi 

thanks for the reply

I use vpn connection manager ppp (generic) not sure what kind it is I am trying to connect to windows server 2003.

i tried the mtu to 1404 but still no go.

What do I put in the server section in connect to server, is it the vpn-xxxx.dyndns.org or the ip address of the server or either, I have tried both to no avail.

Thanks again

thank heavens for the kind people of ubuntu

---

### Post by cmnorton on 2008-04-01
Is this ppp or wireless?

---

### Post by english on 2008-04-02
hi

this is wireless :)

cheers

---

