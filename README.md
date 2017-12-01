# CozmoLetsRobot
Host Anki Cozmo on LetsRobot.tv

## Setup instructions:

Setup the Cozmo SDK on your computer using their instructions:

* http://cozmosdk.anki.com/docs/initial.html#installation

Clone Nocturnal's fork of the runmyrobot scripts:

* git clone https://github.com/Nocturnal42/runmyrobot.git

Copy the files from this repo to the appropriate directories:

* Copy hardware/cozmo.py to runmyrobot/hardware

* Copy tts/cozmo_tts.py to runmyrobot/tts

Edit runmyrobot/letsrobot.sample.conf:

* Enter your owner, robot_id, camera_id from LetsRobot.tv
* change [robot] type=none to type=cozmo
* change [tts] type=none to type=cozmo_tts
* Save file as letsrobot.conf

## Starting Cozmo:

* Using the Cozmo app enter SDK mode and connect your mobile device to the host machine.
* Execute the LetsRobot controller using `python3 controller.py`

## Note for audio streaming on MacOS:

The `startAudioCaptureLinux` function in send_video.py calls ffmpeg with alsa input. If you want to stream audio from your mac use `-f avfoundation -i ":0"` in place of `-f alsa -ar 44100 -ac %d -i hw:%d`

I also recommend changing the audio streaming bitrate from 32k to 128k with `-b:a 128k` in the same ffmpeg call.