---
title: "error while installling"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by tygr88 on 2007-10-19
when i try to install CS 1.6 using wine it gives me this error

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Common Files\\InstallShield\\Professional\\RunTime\\IsProBE.tlb" failed with error 2
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:CoGetClassObject class {00020424-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00020424-0000-0000-c000-000000000046} could be created for context 0x1
err:ole:marshal_object couldn't get IPSFactory buffer for interface {3d8b6331-d8b1-11d2-80c5-00104b1f6cea}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040154
err:ole:CoMarshalInterface Failed to marshal the interface {3d8b6331-d8b1-11d2-80c5-00104b1f6cea}, 80040154
err:ole:marshal_object couldn't get IPSFactory buffer for interface {00000131-0000-0000-c000-000000000046}
err:ole:CoGetClassObject class {00020424-0000-0000-c000-000000000046} not registered
err:ole:CoGetClassObject no class object {00020424-0000-0000-c000-000000000046} could be created for context 0x1
err:ole:marshal_object couldn't get IPSFactory buffer for interface {6494206f-23ea-11d3-88b0-00c04f72f303}
err:ole:StdMarshalImpl_MarshalInterface Failed to create ifstub, hres=0x80040154
err:ole:CoMarshalInterface Failed to marshal the interface {6494206f-23ea-11d3-88b0-00c04f72f303}, 80040154
err:win:WINPOS_GetWinOffset bad hwndFrom = 0x10024

```
i am using wine 0.9.47
i had the same prob with 0.9.41

---

