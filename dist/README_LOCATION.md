User opens website
      ↓
Ask location permission
      ↓
Latitude/Longitude
      ↓
Get District (e.g., Chennai, Coimbatore, Madurai)
      ↓
Show district-specific news
// ---------------
1. navigator.geolocation()  <-- exact location
2. If denied:
      IPinfo Lite
3. If latitude/longitude available:
      Nominatim reverse geocoding

// ------------------

## IPinfo Lite:
React
   ↓
.NET Core API
   ↓
IPinfo API
   ↓
Return location
   ↓
React

// ------------------

Tok : 5e01e077600f5e

curl -H "Authorization: Bearer 5e01e077600f5e" https://api.ipinfo.io/lite/8.8.8.8

Architecture:
User opens website
       │
       ▼
Try Browser Geolocation
       │
       ├── Permission Granted
       │       │
       │       ▼
       │  Latitude & Longitude
       │       │
       │       ▼
       │  Nominatim/OpenCage
       │       │
       │       ▼
       │  District + Suburb + City
       │
       └── Permission Denied
               │
               ▼
            IPinfo
               │
               ▼
        Approximate City/State
Primary: Browser Geolocation → Nominatim/OpenCage (accurate district and suburb).
Fallback: IPinfo (city/state only) if the user declines location access.        