# NOX DRAW — Amir Nagi Edition

## Included
- Multiplayer rooms with 5-character room codes
- Node.js + Express + Socket.IO server (no PeerJS dependency)
- Live drawing, basic shapes, eraser, pan/zoom
- Room chat
- Voice chat using WebRTC audio mesh + public STUN servers
- Upload a gallery image as a shared board background
- Add text to the shared canvas
- PNG export, undo-own-last-item, clear board
- Mobile-friendly canvas with capped DPR and batched point updates
- Footer signature: «طراحی و ساخت امیر ناگی»

## Run locally
Requires Node.js 18+.

```bash
npm install
npm start
```
Open `http://localhost:3000` on devices connected to the same network (for local network testing, use your computer's LAN IP).

## Deploy on Render
1. Create a new **Web Service** from this project repository.
2. Runtime: Node.
3. Build command: `npm install`
4. Start command: `npm start`
5. Render supplies `PORT`; the server reads it automatically.
6. After deployment, open the HTTPS URL.

A `render.yaml` is included as a deployment blueprint.

## Important limitations
- Room state is in server memory. If the server restarts, active rooms and drawings are lost. This first release does not have database persistence.
- The voice system is a peer-to-peer mesh, intended for small rooms (up to 4–6 active voice participants). The room hard limit is 8 people. For larger voice rooms, deploy an SFU such as LiveKit or mediasoup.
- Voice requires HTTPS (or localhost) and microphone permission. Some networks block direct WebRTC paths; a TURN server may be needed for reliable audio on restrictive networks.
- The service host, device, browser, and network determine real FPS and latency. The app is optimized for low overhead, but a fixed FPS is not guaranteed.
- Image backgrounds are sent to all room members and limited to about 4 MB.
- This is a ready-to-deploy project, not an already-hosted public service. You must deploy it to activate its internet URL.
