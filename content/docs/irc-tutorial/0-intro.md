---
title: "Writing an IRC bot"
weight : 0100
menu:
  docs:
    parent: tutorial
---

Internet Relay Chat (IRC) is a simple, text protocol<sup>[[1]](#IRC)</sup>.
This tutorial uses a subset of the IRC protocol to implement a chat bot. 

We'll start with the basics of asynchronous reading and writing, then create a
client library and a simple bot that uses that library, demonstrating tokio core
concepts along the way.  

In this tutorial, we'll use the network utility `socat` for helpful tracing
(and as an SSL proxy) and connect to a hosted IRC service (gitter).  

## IRC account setup

1. [Join our gitter bot community](https://gitter.im/irc-tokio/community)
2. get IRC password from: https://irc.gitter.im/

For the tutorial we'll use environment variables for convenvience:
```bash,ignore
export USER='ultrasaurus_twitter'
export PASS='...redacted...'
```

## Connect using socat

To get a feel for `socat`, let's just connect via `stdin`.  The following 
command takes input from stdin and sends it to `irc.gitter.im` on port `6667`. (`verify=0` turns off ssl verification checks, which we would not want to do for a real client, but is awesome for getting started quick in a tutorial.)  After typing the command below, we need to authenticate quickly or gitter will timeout the connection:

```
echo PASS $PASS
socat -v stdin ssl:irc.gitter.im:6667,verify=0
```

Now, past 

3. Type the following on the command line:

```
socat -v tcp4-listen:1234,reuseaddr,fork ssl:irc.gitter.im:6667,verify=0
```

PASS $PASS

PONG irc.gitter.im



"PASS $PASS\r\nNICK $USER\r\nUSER $USER 0 * $USER\r\n"


PASS $PASS NICK $USER
USER $USER 0 * $USER


PONG irc.gitter.im

socat -v stdin ssl:irc.gitter.im:6667,verify=0


---

<a name="IRC">[1]</a> [RFC 2812](https://tools.ietf.org/html/rfc2812) IRC Client Protocol







