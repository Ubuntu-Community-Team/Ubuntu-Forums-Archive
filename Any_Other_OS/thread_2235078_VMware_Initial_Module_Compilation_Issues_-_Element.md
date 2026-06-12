---
title: "VMware Initial Module Compilation Issues - Elementary OS Luna Trusty"
date: 2014-07-18
forum: Any Other OS
---

### Post by manuleka on 2014-07-18
I've just installed VMWare Workstation 10.0.1 x64 on my Elementary OS Luna 12.04 LTS (Trusty Kernel) and when first fire it up i get the prompt "Before you can run VMware several modules must be compiled and loaded into the running kernel."

When i click Install i get the exclamation sign on the side of the " ! Virtual Network Device" before it says unable to start services and pointed to look into the log below...

can someone help me solve this issue please...

```

2014-07-19T08:11:50.840+12:00| vthread-3| I120: Log for VMware Workstation pid=1081 version=10.0.1 build=build-1379776 option=Release
2014-07-19T08:11:50.840+12:00| vthread-3| I120: The process is 64-bit.
2014-07-19T08:11:50.840+12:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2014-07-19T08:11:50.840+12:00| vthread-3| I120: Host is Linux 3.13.0-32-generic elementary OS Luna
2014-07-19T08:11:50.839+12:00| vthread-3| I120: Msg_Reset:
2014-07-19T08:11:50.839+12:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2014-07-19T08:11:50.839+12:00| vthread-3| I120: ----------------------------------------
2014-07-19T08:11:50.839+12:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2014-07-19T08:11:50.839+12:00| vthread-3| I120: Msg_Reset:
2014-07-19T08:11:50.839+12:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2014-07-19T08:11:50.839+12:00| vthread-3| I120: ----------------------------------------
2014-07-19T08:11:50.839+12:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2014-07-19T08:11:50.839+12:00| vthread-3| I120: PREF Unable to check permissions for preferences file.
2014-07-19T08:11:50.839+12:00| vthread-3| I120: Msg_Reset:
2014-07-19T08:11:50.839+12:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2014-07-19T08:11:50.839+12:00| vthread-3| I120: ----------------------------------------
2014-07-19T08:11:50.839+12:00| vthread-3| I120: PREF Failed to load user preferences.
2014-07-19T08:11:50.840+12:00| vthread-3| W110: Logging to /tmp/vmware-root/vmware-modconfig-1081.log
2014-07-19T08:11:50.846+12:00| vthread-3| I120: Obtaining info using the running kernel.
2014-07-19T08:11:50.846+12:00| vthread-3| I120: Created new pathsHash.
2014-07-19T08:11:50.846+12:00| vthread-3| I120: Setting header path for 3.13.0-32-generic to "/lib/modules/3.13.0-32-generic/build/include".
2014-07-19T08:11:50.846+12:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-19T08:11:50.846+12:00| vthread-3| I120: using /usr/bin/gcc-4.6 for preprocess check
2014-07-19T08:11:50.852+12:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-19T08:11:50.852+12:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-19T08:11:50.949+12:00| vthread-3| I120: Reading in info for the vmmon module.
2014-07-19T08:11:50.949+12:00| vthread-3| I120: Reading in info for the vmnet module.
2014-07-19T08:11:50.949+12:00| vthread-3| I120: Reading in info for the vmblock module.
2014-07-19T08:11:50.949+12:00| vthread-3| I120: Reading in info for the vmci module.
2014-07-19T08:11:50.949+12:00| vthread-3| I120: Reading in info for the vsock module.
2014-07-19T08:11:50.949+12:00| vthread-3| I120: Setting vsock to depend on vmci.
2014-07-19T08:11:50.949+12:00| vthread-3| I120: Invoking modinfo on "vmmon".
2014-07-19T08:11:50.951+12:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-07-19T08:11:50.951+12:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-07-19T08:11:50.953+12:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-19T08:11:50.953+12:00| vthread-3| I120: Invoking modinfo on "vmblock".
2014-07-19T08:11:50.956+12:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-19T08:11:50.956+12:00| vthread-3| I120: Invoking modinfo on "vmci".
2014-07-19T08:11:50.958+12:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-19T08:11:50.958+12:00| vthread-3| I120: Invoking modinfo on "vsock".
2014-07-19T08:11:50.960+12:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-07-19T08:11:50.975+12:00| vthread-3| I120: to be installed: vmnet status: 0
2014-07-19T08:11:50.982+12:00| vthread-3| I120: Obtaining info using the running kernel.
2014-07-19T08:11:50.982+12:00| vthread-3| I120: Setting header path for 3.13.0-32-generic to "/lib/modules/3.13.0-32-generic/build/include".
2014-07-19T08:11:50.982+12:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-19T08:11:50.982+12:00| vthread-3| I120: using /usr/bin/gcc-4.6 for preprocess check
2014-07-19T08:11:50.989+12:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-19T08:11:50.989+12:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-19T08:11:51.092+12:00| vthread-3| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.13.0-32-generic/build/include
2014-07-19T08:11:51.092+12:00| vthread-3| I120: Update kernel header path to /lib/modules/3.13.0-32-generic/build/include
2014-07-19T08:11:51.092+12:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-19T08:11:51.092+12:00| vthread-3| I120: using /usr/bin/gcc-4.6 for preprocess check
2014-07-19T08:11:51.099+12:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-19T08:11:51.100+12:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-19T08:11:51.100+12:00| vthread-3| I120: Found compiler at "/usr/bin/gcc"
2014-07-19T08:11:51.103+12:00| vthread-3| I120: Got gcc version "4.6".
2014-07-19T08:11:51.103+12:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-19T08:11:51.103+12:00| vthread-3| I120: Using user supplied compiler "/usr/bin/gcc".
2014-07-19T08:11:51.106+12:00| vthread-3| I120: Got gcc version "4.6".
2014-07-19T08:11:51.106+12:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-19T08:11:51.112+12:00| vthread-3| I120: Trying to find a suitable PBM set for kernel "3.13.0-32-generic".
2014-07-19T08:11:51.112+12:00| vthread-3| I120: No matching PBM set was found for kernel "3.13.0-32-generic".
2014-07-19T08:11:51.112+12:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-19T08:11:51.112+12:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-19T08:11:51.112+12:00| vthread-3| I120: using /usr/bin/gcc-4.6 for preprocess check
2014-07-19T08:11:51.120+12:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-19T08:11:51.120+12:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-19T08:11:51.121+12:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-19T08:11:51.121+12:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-19T08:11:51.121+12:00| vthread-3| I120: using /usr/bin/gcc-4.6 for preprocess check
2014-07-19T08:11:51.128+12:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-19T08:11:51.128+12:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-19T08:11:51.128+12:00| vthread-3| I120: Using temp dir "/tmp".
2014-07-19T08:11:51.129+12:00| vthread-3| I120: Obtaining info using the running kernel.
2014-07-19T08:11:51.129+12:00| vthread-3| I120: Setting header path for 3.13.0-32-generic to "/lib/modules/3.13.0-32-generic/build/include".
2014-07-19T08:11:51.129+12:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-19T08:11:51.129+12:00| vthread-3| I120: using /usr/bin/gcc-4.6 for preprocess check
2014-07-19T08:11:51.136+12:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-19T08:11:51.136+12:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-19T08:11:51.233+12:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-07-19T08:11:51.235+12:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-19T08:11:51.351+12:00| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-32-generic/misc/vmnet.ko".
2014-07-19T08:11:51.351+12:00| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-07-19T08:11:51.359+12:00| vthread-3| I120: Successfully extracted the vmnet source.
2014-07-19T08:11:51.359+12:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-SqF7G1/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-19T08:11:52.362+12:00| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.

```

---

### Post by steve141 on 2014-07-24
I am using VMware 9 and have the same problem as manuleka.

Any ideas on how to fix this?

2014-07-24T16:50:34.157-08:00| vthread-3| I120: Log for VMware Workstation pid=3961 version=9.0.2 build=build-1031769 option=Release
2014-07-24T16:50:34.157-08:00| vthread-3| I120: The process is 64-bit.
2014-07-24T16:50:34.157-08:00| vthread-3| I120: Host codepage=UTF-8 encoding=UTF-8
2014-07-24T16:50:34.157-08:00| vthread-3| I120: Host is Linux 3.13.0-32-generic Ubuntu 12.04.4 LTS
2014-07-24T16:50:34.157-08:00| vthread-3| I120: Msg_Reset:
2014-07-24T16:50:34.157-08:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/usr/lib/vmware/settings": No such file or directory.
2014-07-24T16:50:34.157-08:00| vthread-3| I120: ----------------------------------------
2014-07-24T16:50:34.157-08:00| vthread-3| I120: PREF Optional preferences file not found at /usr/lib/vmware/settings. Using default values.
2014-07-24T16:50:34.157-08:00| vthread-3| I120: Msg_Reset:
2014-07-24T16:50:34.157-08:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/config": No such file or directory.
2014-07-24T16:50:34.157-08:00| vthread-3| I120: ----------------------------------------
2014-07-24T16:50:34.157-08:00| vthread-3| I120: PREF Optional preferences file not found at /root/.vmware/config. Using default values.
2014-07-24T16:50:34.157-08:00| vthread-3| I120: Msg_Reset:
2014-07-24T16:50:34.157-08:00| vthread-3| I120: [msg.dictionary.load.openFailed] Cannot open file "/root/.vmware/preferences": No such file or directory.
2014-07-24T16:50:34.157-08:00| vthread-3| I120: ----------------------------------------
2014-07-24T16:50:34.157-08:00| vthread-3| I120: PREF Failed to load user preferences.
2014-07-24T16:50:34.158-08:00| vthread-3| W110: Logging to /tmp/vmware-root/vmware-modconfig-3961.log
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Reading in info for the vmmon module.
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Reading in info for the vmnet module.
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Reading in info for the vmblock module.
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Reading in info for the vmci module.
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Reading in info for the vsock module.
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Setting vsock to depend on vmci.
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Created new pathsHash.
2014-07-24T16:50:34.171-08:00| vthread-3| I120: Invoking modinfo on "vmmon".
2014-07-24T16:50:34.174-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.174-08:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-07-24T16:50:34.176-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.176-08:00| vthread-3| I120: Invoking modinfo on "vmblock".
2014-07-24T16:50:34.178-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.178-08:00| vthread-3| I120: Invoking modinfo on "vmci".
2014-07-24T16:50:34.181-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.181-08:00| vthread-3| I120: Invoking modinfo on "vsock".
2014-07-24T16:50:34.183-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-07-24T16:50:34.196-08:00| vthread-3| I120: Obtaining info using the running kernel.
2014-07-24T16:50:34.196-08:00| vthread-3| I120: Setting header path for 3.13.0-32-generic to "/lib/modules/3.13.0-32-generic/build/include".
2014-07-24T16:50:34.196-08:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-24T16:50:34.196-08:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-24T16:50:34.196-08:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-24T16:50:34.204-08:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-24T16:50:34.204-08:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-24T16:50:34.345-08:00| vthread-3| I120: Kernel header path retrieved from FileEntry: /lib/modules/3.13.0-32-generic/build/include
2014-07-24T16:50:34.345-08:00| vthread-3| I120: Update kernel header path to /lib/modules/3.13.0-32-generic/build/include
2014-07-24T16:50:34.345-08:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-24T16:50:34.345-08:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-24T16:50:34.345-08:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-24T16:50:34.353-08:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-24T16:50:34.353-08:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-24T16:50:34.354-08:00| vthread-3| I120: Found compiler at "/usr/bin/gcc"
2014-07-24T16:50:34.357-08:00| vthread-3| I120: Got gcc version "4.6".
2014-07-24T16:50:34.357-08:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-24T16:50:34.357-08:00| vthread-3| I120: Using user supplied compiler "/usr/bin/gcc".
2014-07-24T16:50:34.361-08:00| vthread-3| I120: Got gcc version "4.6".
2014-07-24T16:50:34.361-08:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-24T16:50:34.366-08:00| vthread-3| I120: Trying to find a suitable PBM set for kernel "3.13.0-32-generic".
2014-07-24T16:50:34.367-08:00| vthread-3| I120: No matching PBM set was found for kernel "3.13.0-32-generic".
2014-07-24T16:50:34.367-08:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-24T16:50:34.367-08:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-24T16:50:34.367-08:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-24T16:50:34.374-08:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-24T16:50:34.374-08:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-24T16:50:34.374-08:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-24T16:50:34.386-08:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-24T16:50:34.386-08:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-24T16:50:34.386-08:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-24T16:50:34.394-08:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-24T16:50:34.394-08:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-24T16:50:34.394-08:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-24T16:50:34.394-08:00| vthread-3| I120: Using temp dir "/tmp".
2014-07-24T16:50:34.395-08:00| vthread-3| I120: Invoking modinfo on "vmmon".
2014-07-24T16:50:34.398-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.398-08:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-07-24T16:50:34.401-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.401-08:00| vthread-3| I120: Invoking modinfo on "vmblock".
2014-07-24T16:50:34.403-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.403-08:00| vthread-3| I120: Invoking modinfo on "vmci".
2014-07-24T16:50:34.406-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:50:34.579-08:00| vthread-3| I120: Setting destination path for vmmon to "/lib/modules/3.13.0-32-generic/misc/vmmon.ko".
2014-07-24T16:50:34.579-08:00| vthread-3| I120: Extracting the vmmon source from "/usr/lib/vmware/modules/source/vmmon.tar".
2014-07-24T16:50:34.585-08:00| vthread-3| I120: Successfully extracted the vmmon source.
2014-07-24T16:50:34.585-08:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-ldCbIW/vmmon-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-24T16:50:36.147-08:00| vthread-3| I120: Successfully built vmmon.  Module is currently at "/tmp/modconfig-ldCbIW/vmmon.o".
2014-07-24T16:50:36.147-08:00| vthread-3| I120: Found the vmmon symvers file at "/tmp/modconfig-ldCbIW/vmmon-only/Module.symvers".
2014-07-24T16:50:36.147-08:00| vthread-3| I120: Installing vmmon from /tmp/modconfig-ldCbIW/vmmon.o to /lib/modules/3.13.0-32-generic/misc/vmmon.ko.
2014-07-24T16:50:36.148-08:00| vthread-3| I120: Registering file "/lib/modules/3.13.0-32-generic/misc/vmmon.ko".
2014-07-24T16:50:36.602-08:00| vthread-3| I120: "/usr/lib/vmware-installer/2.1.0/vmware-installer" exited with status 0.
2014-07-24T16:50:36.602-08:00| vthread-3| I120: Registering file "/usr/lib/vmware/symvers/vmmon-3.13.0-32-generic".
2014-07-24T16:50:37.025-08:00| vthread-3| I120: "/usr/lib/vmware-installer/2.1.0/vmware-installer" exited with status 0.
2014-07-24T16:50:37.027-08:00| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-32-generic/misc/vmnet.ko".
2014-07-24T16:50:37.027-08:00| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-07-24T16:50:37.034-08:00| vthread-3| I120: Successfully extracted the vmnet source.
2014-07-24T16:50:37.034-08:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-ldCbIW/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-24T16:50:38.312-08:00| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.
2014-07-24T16:50:38.314-08:00| vthread-3| I120: Setting destination path for vmblock to "/lib/modules/3.13.0-32-generic/misc/vmblock.ko".
2014-07-24T16:50:38.314-08:00| vthread-3| I120: Extracting the vmblock source from "/usr/lib/vmware/modules/source/vmblock.tar".
2014-07-24T16:50:38.322-08:00| vthread-3| I120: Successfully extracted the vmblock source.
2014-07-24T16:50:38.323-08:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-ldCbIW/vmblock-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-24T16:50:39.545-08:00| vthread-3| W110: Failed to build vmblock.  Failed to execute the build command.
2014-07-24T16:50:39.547-08:00| vthread-3| I120: Setting destination path for vmci to "/lib/modules/3.13.0-32-generic/misc/vmci.ko".
2014-07-24T16:50:39.547-08:00| vthread-3| I120: Extracting the vmci source from "/usr/lib/vmware/modules/source/vmci.tar".
2014-07-24T16:50:39.556-08:00| vthread-3| I120: Successfully extracted the vmci source.
2014-07-24T16:50:39.557-08:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-ldCbIW/vmci-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-24T16:50:40.637-08:00| vthread-3| W110: Failed to build vmci.  Failed to execute the build command.
2014-07-24T16:51:04.349-08:00| vthread-3| I120: Validating path "/lib/modules/3.13.0-32-generic/build/include" for kernel release "3.13.0-32-generic".
2014-07-24T16:51:04.349-08:00| vthread-3| I120: Failed to find /lib/modules/3.13.0-32-generic/build/include/linux/version.h
2014-07-24T16:51:04.349-08:00| vthread-3| I120: /lib/modules/3.13.0-32-generic/build/include/linux/version.h not found, looking for generated/uapi/linux/version.h instead.
2014-07-24T16:51:04.357-08:00| vthread-3| I120: Preprocessed UTS_RELEASE, got value "3.13.0-32-generic".
2014-07-24T16:51:04.357-08:00| vthread-3| I120: The header path "/lib/modules/3.13.0-32-generic/build/include" for the kernel "3.13.0-32-generic" is valid.  Whoohoo!
2014-07-24T16:51:04.357-08:00| vthread-3| I120: The GCC version matches the kernel GCC minor version like a glove.
2014-07-24T16:51:04.357-08:00| vthread-3| I120: Using temp dir "/tmp".
2014-07-24T16:51:04.358-08:00| vthread-3| I120: Invoking modinfo on "vmmon".
2014-07-24T16:51:04.361-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 0.
2014-07-24T16:51:04.361-08:00| vthread-3| I120: Invoking modinfo on "vmnet".
2014-07-24T16:51:04.364-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:51:04.364-08:00| vthread-3| I120: Invoking modinfo on "vmblock".
2014-07-24T16:51:04.366-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:51:04.366-08:00| vthread-3| I120: Invoking modinfo on "vmci".
2014-07-24T16:51:04.369-08:00| vthread-3| I120: "/sbin/modinfo" exited with status 256.
2014-07-24T16:51:04.549-08:00| vthread-3| I120: Setting destination path for vmnet to "/lib/modules/3.13.0-32-generic/misc/vmnet.ko".
2014-07-24T16:51:04.550-08:00| vthread-3| I120: Extracting the vmnet source from "/usr/lib/vmware/modules/source/vmnet.tar".
2014-07-24T16:51:04.556-08:00| vthread-3| I120: Successfully extracted the vmnet source.
2014-07-24T16:51:04.556-08:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-ij4vUE/vmnet-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-24T16:51:05.830-08:00| vthread-3| W110: Failed to build vmnet.  Failed to execute the build command.
2014-07-24T16:51:05.832-08:00| vthread-3| I120: Setting destination path for vmblock to "/lib/modules/3.13.0-32-generic/misc/vmblock.ko".
2014-07-24T16:51:05.832-08:00| vthread-3| I120: Extracting the vmblock source from "/usr/lib/vmware/modules/source/vmblock.tar".
2014-07-24T16:51:05.840-08:00| vthread-3| I120: Successfully extracted the vmblock source.
2014-07-24T16:51:05.840-08:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-ij4vUE/vmblock-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-24T16:51:06.996-08:00| vthread-3| W110: Failed to build vmblock.  Failed to execute the build command.
2014-07-24T16:51:06.998-08:00| vthread-3| I120: Setting destination path for vmci to "/lib/modules/3.13.0-32-generic/misc/vmci.ko".
2014-07-24T16:51:06.998-08:00| vthread-3| I120: Extracting the vmci source from "/usr/lib/vmware/modules/source/vmci.tar".
2014-07-24T16:51:07.007-08:00| vthread-3| I120: Successfully extracted the vmci source.
2014-07-24T16:51:07.007-08:00| vthread-3| I120: Building module with command "/usr/bin/make -j8 -C /tmp/modconfig-ij4vUE/vmci-only auto-build HEADER_DIR=/lib/modules/3.13.0-32-generic/build/include CC=/usr/bin/gcc IS_GCC_3=no"
2014-07-24T16:51:08.290-08:00| vthread-3| W110: Failed to build vmci.  Failed to execute the build command.

---

### Post by manuleka on 2014-07-25
This seems to be an issue with Kernels for Ubuntu 13.10+ i reverted back to kernel 3.8 (Ubuntu 13.04) and VMWare Works fine... probably the best fix is to upgrade to latest Workstation 10.0.2 if you want to stay with latest kernel

---

### Post by steve141 on 2014-07-25
> **manuleka said:**
> This seems to be an issue with Kernels for Ubuntu 13.10+ i reverted back to kernel 3.8 (Ubuntu 13.04) and VMWare Works fine... probably the best fix is to upgrade to latest Workstation 10.0.2 if you want to stay with latest kernel

I should have thought twice before upgrading.  

How do I get back to the previous kernel?   Is there an UNDO button?

---

### Post by manuleka on 2014-07-25
on grub (boot selection) select the previous version(s) option and opt for kernel 3.8 or lower

---

### Post by steve141 on 2014-07-25
manuleka,
Will that make it a permanent roll back or will I have to select it every time?
Thanks

---

### Post by manuleka on 2014-07-25
remove the latest/later kernel(s) once you're logged in to that previous kernel

---

### Post by steve141 on 2014-07-25
manuleka
Cool thanks!

---

