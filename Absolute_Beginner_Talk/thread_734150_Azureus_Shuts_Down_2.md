---
title: "Azureus Shuts Down 2"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Lourie2 on 2008-03-24
I am also experiencing that Azureus opens after installation and then closes immediately.  I receive the following when I enter Azureus in the terminal:

Code:
lourie@lourie-IBM:~$ azureus
DEBUG::Mon Mar 24 18:27:51 GMT 2008::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::-1:
  No SSL provider available
    SESecurityManager::initialise::-1,ConfigurationChecker::setSystemProperties::-1,ConfigurationManager::initialise::-1,ConfigurationManager::getInstance::-1,LoggerImpl::init::-1,Logger::<clinit>::-1,Class::initializeClass::-1,Logger::isEnabled::-1,StartServer::<init>::-1,Main::<init>::-1,Main::main::-1
DEBUG::Mon Mar 24 18:27:52 GMT 2008::org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl::initialise::-1:
  No SSL provider available
    SESecurityManager::initialise::-1,CryptoManagerImpl::<init>::-1,CryptoManagerImpl::getSingleton::-1,CryptoManagerFactory::getSingleton::-1,AzureusCoreImpl::<init>::-1,AzureusCoreImpl::create::-1,AzureusCoreFactory::create::-1,Main::<init>::-1,Main::main::-1
DEBUG::Mon Mar 24 18:27:58 GMT 2008::com.aelitis.azureus.core.networkmanager.impl.tcp.VirtualChannelSelectorImpl::select::-1:
  VirtualChannelSelector: No progress for op 1: listener = class com.aelitis.azureus.core.clientmessageservice.impl.NonBlockingReadWriteService$2, count = 10, socket: open = true, connected = true
    VirtualChannelSelector::select::-1,NonBlockingReadWriteService$1::runSupport::-1,AEThread::run::-1
Aborted (core dumped)
lourie@lourie-IBM:~$

Please help!

---

### Post by POW R TOC H on 2008-03-24
I think that that is some kind of Java mumbo-jumbo, after all, Azureus is written in java. It didn't work for me either, until I reinstalled the newest Java Runtime. Try doing that.

---

