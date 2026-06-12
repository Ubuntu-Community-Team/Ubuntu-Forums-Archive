---
title: "PartySip installation iusse"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by eisenmeteor on 2008-02-27
Hi everyone.

I'm trying to install partysip on the Ubuntu distro, but I've the following errors when I launch  the 'make' command:

../../partysip-2.2.3/src/osip_msg.c: In function ‘osip_msg_build_response’:
../../partysip-2.2.3/src/osip_msg.c:91: error: incompatible type for argument 1 of ‘osip_list_eol’
../../partysip-2.2.3/src/osip_msg.c:96: error: incompatible type for argument 1 of ‘osip_list_get’
../../partysip-2.2.3/src/osip_msg.c:100: error: incompatible type for argument 1 of ‘osip_list_add’
../../partysip-2.2.3/src/osip_msg.c:122: error: incompatible type for argument 1 of ‘osip_list_get’
../../partysip-2.2.3/src/osip_msg.c:200: error: incompatible type for argument 1 of ‘osip_list_eol’
../../partysip-2.2.3/src/osip_msg.c:204: error: incompatible type for argument 1 of ‘osip_list_get’
../../partysip-2.2.3/src/osip_msg.c:207: error: incompatible type for argument 1 of ‘osip_list_add’
../../partysip-2.2.3/src/osip_msg.c: In function ‘osip_msg_sfp_build_response_osip_to_forward’:
../../partysip-2.2.3/src/osip_msg.c:233: error: incompatible type for argument 1 of ‘osip_list_get’
../../partysip-2.2.3/src/osip_msg.c:239: error: incompatible type for argument 1 of ‘osip_list_remove’
../../partysip-2.2.3/src/osip_msg.c: In function ‘_osip_message_set_topheader’:
../../partysip-2.2.3/src/osip_msg.c:353: error: incompatible type for argument 1 of ‘osip_list_add’
../../partysip-2.2.3/src/osip_msg.c: In function ‘osip_msg_default_build_request_osip_to_forward’:
../../partysip-2.2.3/src/osip_msg.c:430: error: incompatible type for argument 1 of ‘osip_list_add’
../../partysip-2.2.3/src/osip_msg.c:468: error: incompatible type for argument 1 of ‘osip_list_remove’
../../partysip-2.2.3/src/osip_msg.c:502: error: incompatible type for argument 1 of ‘osip_list_add’
../../partysip-2.2.3/src/osip_msg.c:508: error: incompatible type for argument 1 of ‘osip_list_size’
../../partysip-2.2.3/src/osip_msg.c: In function ‘osip_msg_modify_ack_osip_to_be_forwarded’:
../../partysip-2.2.3/src/osip_msg.c:671: error: incompatible type for argument 1 of ‘osip_list_add’
../../partysip-2.2.3/src/osip_msg.c:705: error: incompatible type for argument 1 of ‘osip_list_remove’
../../partysip-2.2.3/src/osip_msg.c:719: error: incompatible type for argument 1 of ‘osip_list_size’
../../partysip-2.2.3/src/osip_msg.c: In function ‘osip_msg_build_cancel’:
../../partysip-2.2.3/src/osip_msg.c:782: error: incompatible type for argument 1 of ‘osip_list_add’


How could I solve this iusse?
 I'm using libosip2-3 version 2.2.2-3.1

Please help me

---

### Post by eisenmeteor on 2008-02-27
I've just solved out the iusse... libosip version was too new

---

