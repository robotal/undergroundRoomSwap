
# Underground Room Swap

---

Name: Tal Davidi

Date: April 29th, 2017

Project Topic: A website for listing room-swap requests facilitated by exchange
of money.

URL: https://ter.ps/underground

---


### 1. Data Format and Storage

Data point fields:

Listing
- `Field 1`:     Gender             `Type`: String
- `Field 2`:     Listing Price      `Type`: Number
- `Field 3`:     Hall Name          `Type`: String
- `Field 4`:     Number of Rooms    `Type`: Number
- `Field 5`:     Free Spots         `Type`: [RoomOpening]
- `Field 6`:     Room Number        `Type`: Number
- `Field 7`:     Bathrooms          `Type`: Number
- `Field 8`:     Contact Point          `Type`: String


RoomOpening
- `Field 1`:     Vacancies       `Type`: Number
- `Field 2`:     Total Beds       `Type`: Number
Schema:
```javascript
Listing: {
   gender: {
       type: String,
       required: true
   },
   price: {
       type: Number,
       required: true
   },
   hallName: {
       type: String,
       required: true
   },
   numberOfRooms: {
       type: Number,
       required: true
   },
   freeSpots: {
       type: [RoomOpening],
       required: true
   },
   roomNumber: {
       type: String,
       required: true
   },
   bathrooms: {
       type: Number
       required: true
   }
}

RoomOpening: {
  vacancies: {
    type: Number,
    required: true
  },
  totalBeds: {
    type: Number,
    require: true
  }
}
```

### 2. Add New Data

HTML form route: `/list`

POST endpoint route: `/api/newListing`

Example Node.js POST request to endpoint:
```javascript
var request = require("request");

var options = {
    method: 'POST',
    url: 'http://localhost:3000/api/...',
    headers: {
        'content-type': 'application/x-www-form-urlencoded'
    },
    form: {
       gender: 'male',
       price: '100',
       hallName: 'Centreville',
       numberOfRooms: '2',
       roomNumber: '123',
       bathrooms: '0',
       'leaving-1': '2',
       'beds-1': '4',
       'leaving-2': '2',
       'leaving-2': '2'
    }
};

request(options, function (error, response, body) {
  if (error) throw new Error(error);

  console.log(body);
});
```

### 3. View Data

GET endpoint route: `/api/getListings`

### 4. Search Data

Search Field: `Hall Name`

### 5. Navigation Pages

Navigation Filters
1. Community Name -> `/community/:communityName`
2. Random Listing -> `/random`
3. Top Halls -> `/popular`
4. Cheapest -> `/cheapest`
5. Most Expensive -> `/expensive`
